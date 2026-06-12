---
title: "Problem with wxglade, and lxml on Python 2.6"
date: 2011-04-15
forum: Installation &amp; Upgrades
---

### Post by akm3 on 2011-04-15
Hi,

I have been recently facing some problems with my default Python installation (Python 2.6.5 (r265:79063, Apr 16 2010, 13:09:56))on Ubuntu 10.04.

It seems that there is something wrong with "wxglade", which gives me the following Error when I try to start it:

```

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/wxglade/wxglade.py", line 160, in <module>
    run_main()
  File "/usr/lib/python2.6/dist-packages/wxglade/wxglade.py", line 147, in run_main
    import main
  File "/usr/lib/python2.6/ihooks.py", line 406, in import_module
    q, tail = self.find_head_package(parent, str(name))
  File "/usr/lib/python2.6/ihooks.py", line 449, in find_head_package
    raise ImportError, "No module named " + qname
ImportError: No module named main

```

This has made further problems for me using python's xml library. As an example, trying to call xml.etree.ElementTree.parse() on an XML file, results in the following Error:
```

Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.6/xml/etree/ElementTree.py", line 862, in parse
    tree.parse(source, parser)
  File "/usr/lib/python2.6/xml/etree/ElementTree.py", line 586, in parse
    parser.feed(data)
  File "/usr/lib/python2.6/xml/etree/ElementTree.py", line 1245, in feed
    self._parser.Parse(data, 0)
  File "/usr/lib/python2.6/xml/etree/ElementTree.py", line 1177, in _start_list
    tag = fixname(tag)
  File "/usr/lib/python2.6/xml/etree/ElementTree.py", line 1164, in _fixname
    self._names[key] = name = self._fixtext(name)
  File "/usr/lib/python2.6/xml/etree/ElementTree.py", line 1152, in _fixtext
    return _encode(text, "ascii")
  File "/usr/lib/python2.6/xml/etree/ElementTree.py", line 751, in _encode
    return s.encode(encoding)
  File "/usr/lib/python2.6/encodings/__init__.py", line 100, in search_function
    level=0)
TypeError: import_module() got an unexpected keyword argument 'level'

```

I also get difficulty runnig SPE, with an Error like this:
```

Spe Error: Please install the right version of wxPython: 2.6.1.0.
No module named wx

SPE v0.8.4.h (c)2003-2008 www.stani.be

If spe fails to start:
 - type "python SPE.py --debug > debug.txt 2>&1" at the command prompt
   (or if you use tcsh: "python SPE.py --debug >& debug.txt")
 - send debug.txt with some info to spe.stani.be[at]gmail.com
 
Traceback (most recent call last):
  File "/usr/bin/spe", line 53, in <module>
    import ConfigParser, sys, os, wx
  File "/usr/lib/python2.6/ihooks.py", line 406, in import_module
    q, tail = self.find_head_package(parent, str(name))
  File "/usr/lib/python2.6/ihooks.py", line 449, in find_head_package
    raise ImportError, "No module named " + qname
ImportError: No module named wx

```

I'm not sure if the problems with all of these is with wxglade, but I cannot re-install the package, which gives me the following error:
```

E: python-wxglade: subprocess installed post-installation script returned error exit status 1
E: spe: dependency problems - leaving unconfigured

```

Among all these problems, I'm very much frustrated with the xml module not working properly.

Has anybody had similar problems, or an idea to solve this?

---

