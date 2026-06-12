---
title: "pythoncard 0.8.2 for ubuntu 9.10"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by pr0grammer on 2010-03-08
I cannot properly install pythoncard 0.8.2 in ubuntu 9.10.

I need to use pythoncard 0.8.2 for the layout editor. version 0.8.1-8.1ubuntu1, which is available through the package manage, does not have a layout editor.

I was able to get pythoncard 0.8.2 working in ubuntu 8.04 simply by running the setup.py file. However i have noticed the install location for python in ubuntu 8.04 is different from the location in ubuntu 9.10. I have been looking at the "installed files" option in the package manager to try to figure it out. I have also check python.org and ubuntu.com for installation documentation. Could someone please point me to documentation on how ubuntu 9.10 expects python to be installed as well as how it expects add ons such as wx and pythoncard to be installed?

Thank you.

---

### Post by pr0grammer on 2010-03-09
additional information:

I have a python program i am porting over for a company. I ported onto ubuntu 8.10 (i installed pythoncard 0.8.2 from source and wx 2.8 10.1 from the repository). However I cannot get the program to work in 9.10. When I run the program using pythoncard from the repository(which installs wx 2.6-0) I get the following output:

<code>

Traceback (most recent call last):
  File "DTS_HMI.py", line 1343, in <module>
    app = model.Application(DTS_HMI)
  File "/usr/lib/pymodules/python2.6/PythonCard/model.py", line 365, in __init__
    wx.App.__init__(self, 0)
  File "/usr/lib/python2.6/dist-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7700, in __init__
    self._BootstrapApp()
  File "/usr/lib/python2.6/dist-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7352, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
  File "/usr/lib/pymodules/python2.6/PythonCard/model.py", line 417, in OnInit
    self._initBackgrounds(self.resource)
  File "/usr/lib/pymodules/python2.6/PythonCard/model.py", line 410, in _initBackgrounds
    bg = self.frameClass(None, bgRsrc)
  File "/usr/lib/pymodules/python2.6/PythonCard/model.py", line 640, in __init__
    self._initLayout(aBgRsrc.components)
  File "/usr/lib/pymodules/python2.6/PythonCard/model.py", line 954, in _initLayout
    self.components[rsrc.name] = rsrc
  File "/usr/lib/pymodules/python2.6/PythonCard/model.py", line 98, in __setitem__
    control = component.ComponentFactory().createComponent(self.parent, self.parent.panel, item)
  File "/usr/lib/pymodules/python2.6/PythonCard/component.py", line 302, in createComponent
    component = clazz( aParent, aResource )
  File "/usr/lib/pymodules/python2.6/PythonCard/components/bitmapcanvas.py", line 96, in __init__
    widget.Widget.__init__(self, aParent, aResource)
  File "/usr/lib/pymodules/python2.6/PythonCard/widget.py", line 77, in __init__
    self._setBackgroundColor(self._resource.backgroundColor)
  File "/usr/lib/pymodules/python2.6/PythonCard/components/bitmapcanvas.py", line 134, in _setBackgroundColor
    brush.SetColour(aColor)
  File "/usr/lib/python2.6/dist-packages/wx-2.6-gtk2-unicode/wx/_gdi.py", line 447, in SetColour
    return _gdi_.Brush_SetColour(*args, **kwargs)
TypeError: Expected a wxColour object or a string containing a colour name or '#RRGGBB'.

</code>

the program was running under pythoncard 0.8.2 and wx 2.8.10.2. Any help would be greatly appreciated.

---

### Post by siggi2 on 2010-03-16
Maybe this helps: I had similar messages, lots of lines, with a final:
"TypeError: Expected a wxColour object or a string containing a colour name or '#RRGGBB'."
like you, when running a pythoncard program* on Ubuntu 9.10, python 2.6.4~rc... and appropriate pythoncard. So, I searched for 'color' in my resource file and replaced 
> 'foregroundColor':(255, 0, 0, 255),
(the smiley should be replaced with 'colon parenthesis open')
with
> 'foregroundColor':'red', 

That did it: no more error messages, the program runs fine, except...
...the pythoncard object (gauge bar) had not the color red it should, it was Ubuntu-brown. Even changing its color using the resources editor did not change the color of the gauge bar, it stays stubornly brown.

I guess, there is something messy about Ubuntu 9.10. and pythoncard 0.8.1

cheers,

siggi2

P.S. *: no error messages and color problems with this program on python2.5 and appropriate pythoncard (Windows XP Home).

---

### Post by siggi2 on 2010-03-16
Hi pr0grammer, why don't you report this to the launchpad?
Seems to be as serious as the boost libraries failure with VPython and Ubuntu 9.10:
[https://bugs.launchpad.net/ubuntu/+source/python-visual/+bug/429015](https://bugs.launchpad.net/ubuntu/+source/python-visual/+bug/429015)

Cheers,

siggi2

---

### Post by siggi2 on 2010-03-17
here is my detailed report:

*** 1 ***
This works fine, no error messages and color problems as indicated above:
- on MS WindowsXP Home:
- python 2.5.1 plus wxpython 2.8.7.1 plus pythoncard 0.8.2

*** 2 ***
This gives the error messages and problems as stated above:
- on Ubuntu 9.10:
- python 2.6.4 plus python-wxgtk 2.6.3 plus python-wxgtk2.8.10 plus pythoncard 0.8.1 (depending on wxgtk2.6)

It does not help to install, in addition, from Debian unstable pythoncard 0.8.2 (this package depends on wxgtk 2.6, not on 2.8 as in Windows)

So, for the time being, whenever I get error messages similar to posting no 2, I resort to changing 
'foregroundColor'255, 0, 0, 255) (or similar lines in a *.rsrc.py file)
to
'foregroundColor':'red', (or something similar)

It is a pity that these programs run better in MS Windows than in Ubuntu :lolflag:

---

### Post by siggi2 on 2010-04-05
> **pr0grammer said:**
> ...Could someone please point me to documentation on how ubuntu 9.10 expects python to be installed as well as how it expects add ons such as wx and pythoncard to be installed?

Thank you.

Here is the solution of your problem (if it is still your problem):

[http://www.manning-sandbox.com/thread.jspa?threadID=37285&tstart=0](http://www.manning-sandbox.com/thread.jspa?threadID=37285&tstart=0)

---

