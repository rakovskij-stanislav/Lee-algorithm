# Lee-algorithm

This is [his](https://github.com/CorvoOrc) implementation Lee algorithm.
More information about this method: https://en.wikipedia.org/wiki/Lee_algorithm

Changes:
- Removed dependency on "Queue"
- python2.7 -> python3
- Works faster (x2.62 times) without "queue"

Anti-queue liberation is:
- q = Queue() => q = []
- q.empty() => len(q)==0
- a = q.get() => a = q[0]; del q[0]
- q.put(smth) => q.append(smth)

BE CAREFUL! Perfomance boost only for python3, not python2.7 (~23 sec both variants using py2.7)

Benchmarks on Intel i5 2450M:
```
python3
Python 3.5.2 (default, Nov 17 2016, 17:05:23) 
[GCC 5.4.0 20160609] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import leeNew, timeit
>>> timeit.timeit(leeNew.start, number=100000)
11.01934291300131
```
```
python3
Python 3.5.2 (default, Nov 17 2016, 17:05:23) 
[GCC 5.4.0 20160609] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import leeIld, timeit
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named 'leeIld'
>>> import leeOld, timeit
>>> timeit.timeit(leeOld.start, number=100000)
28.849706049993983
```
