---
title: "Installing nltk + Python 2.5 (Small problem)"
date: 2007-04-18
forum: Installation &amp; Upgrades
---

### Post by Darkness3477 on 2007-04-18
Hi, I'm trying to install nltk (A Python module for Natural Language Processing) which reccomends using 2.5 So I've download and done the following to install:
	cd Python-2.5
	./configure
	make
	sudo make install

However, when I run python -V it says I'm still using Python 2.4.3
I'm gussing I need to update the enviormental variable path or what not, but I'm not exactly sure how to do that.

Also, I've had trouble install 'numpy' which is another Python module. I followed the instructions [http://nltk.sourceforge.net/install-lite_unix.html](http://nltk.sourceforge.net/install-lite_unix.html) and it all seemed to work.

However, when I ran a few tests in IDLE it says I don't have it. 
This is the exact error:
```
from nltk_lite.corpora import brown
Traceback (most recent call last):
  File "<pyshell#1>", line 1, in ?
    from nltk_lite.corpora import brown
  File "/usr/lib/python2.4/site-packages/nltk_lite/corpora/brown.py", line 40, in ?
    from nltk_lite.tag import string2tags, string2words
  File "/usr/lib/python2.4/site-packages/nltk_lite/tag/__init__.py", line 136, in ?
    from unigram import *
  File "/usr/lib/python2.4/site-packages/nltk_lite/tag/unigram.py", line 16, in ?
    from nltk_lite.probability import FreqDist, ConditionalFreqDist
  File "/usr/lib/python2.4/site-packages/nltk_lite/probability.py", line 39, in ?
    import types, math, numpy
ImportError: No module named numpy
```

Any help with this would be greatly appreciated, as I'd really like to start having a play with the tutorial I found which uses nltk

P.S. I have a feeling that using 2.5 might fix the Numpy problem, but I'm not entirely sure.

---

