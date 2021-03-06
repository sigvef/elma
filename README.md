# Elma Python Library

[![Travis](https://img.shields.io/travis/sigvef/elma.svg)](https://travis-ci.org/sigvef/elma/)
[![PyPI](https://img.shields.io/pypi/v/elma.svg)](https://pypi.python.org/pypi/elma/)
![Licence](https://img.shields.io/pypi/l/elma.svg)

Elma Python Library is a python library for manipulating Elasto Mania files.
Currently, it supports simple level and replay manipulation.


## Documentation

[Documentation is available at elma-python-library.readthedocs.org](https://elma-python-library.readthedocs.org).


## Installation

```
pip install elma
```


## Usage


### Creating a simple level
```python
from elma import Level, Obj, Picture, Point, Polygon

level = Level()
level.name = 'My first level'
level.polygons = [
    Polygon([Point(-10, -10),
             Point(10, -10),
             Point(10, 10),
             Point(-10, 10)]),
]
level.objects = [
    Obj(Point(0, 0), Obj.START),
    Obj(Point(0, 10), Obj.FOOD, gravity=Obj.GRAVITY_UP),
    Obj(Point(0, 0), Obj.FLOWER),
]
level.pictures = [
    Picture(Point(2, 8), picture_name='flag'),
]
```

The above snippet defines a simple level that looks like this:

![](http://i.imgur.com/cl8SJgk.png)


### Loading a level from a file
```python
from elma import Level

level = Level.load('mylevel.lev')
```


### Saving a level to a file
```python
level.save('mylevel.lev')
```


### Merging level top10s
```python
from elma import Level

level1 = Level.load('mylevel1.lev')
level2 = Level.load('mylevel2.lev')

if level1 == level2:
    level1.top10.merge(level2.top10)
    level1.save('mylevel.lev')
```


### Loading a replay from a file
```python
from elma import Replay

replay = Replay.load('myreplay.rec')
```


### Saving a replay to a file
```python
replay.save('myreplay.rec')
```


## Development setup

```
virtualenv venv
. venv/bin/activate
make setup
```


## Running tests

```
make test
```


## Linting

To lint the project, do:

```
make lint
```

## Type checking

To run static type checking with mypy, do:

```
make mypy
```

## Contributing

Pull requests welcome!
