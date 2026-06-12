---
title: "podnova not working after upgrade to Gutsy"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by madjo on 2007-10-19
I have tried to find a solution for this problem, but I've yet to find one that works.

Here's the deal.
I just upgraded to Xubuntu Gutsy.
And I went to start the programs that I use daily, and one of them is PodNova version 2.2.
But instead of my list of podcasts I'm surprised with this message:

```
/usr/local/bin/PodNova-2.2/gui/tree.py:6: DeprecationWarning: The wxPython compatibility package is no longer automatically generated or actively maintained.  Please switch to the wx package as soon as possible.
  from wxPython.wx import *
Traceback (most recent call last):
  File "iPodderGui.py", line 3522, in <module>
    main()
  File "iPodderGui.py", line 3512, in main
    myApp = iPodderGui(ipodder,options)
  File "iPodderGui.py", line 738, in __init__
    wx.App.__init__(self, False, None)
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 7823, in __init__
    self._BootstrapApp()
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 7420, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
  File "iPodderGui.py", line 1504, in OnInit
    self.InitHooks()
  File "iPodderGui.py", line 1852, in InitHooks
    for att, method in inspect.getmembers(self, inspect.ismethod): 
  File "/usr/lib/python2.5/inspect.py", line 206, in getmembers
    value = getattr(object, key)
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 9445, in GetAcceleratorTable
    return _core_.Window_GetAcceleratorTable(*args, **kwargs)
TypeError: in method 'Window_GetAcceleratorTable', expected argument 1 of type 'wxWindow *'
```


Now I've tried all sorts of things, including the Feisty repos of WXpython itself, but that didn't solve it either.

Can someone help me in the right direction, please? OR should I file in a bug report on this?

BTW, I also tried a fresh install of icePodder (from their svn), but that one fails with this message:
```
*** glibc detected *** python: free(): invalid pointer: 0x0979e220 ***
```

Or when run as root:
```
 glibc detected *** python: double free or corruption (out)
```

---

### Post by jrasmussen0 on 2007-10-19
I was able to get icepodder to work which seems to be a more active split from podnova.

svn co [https://icepodder.svn.sourceforge.net/svnroot/icepodder](https://icepodder.svn.sourceforge.net/svnroot/icepodder)

---

### Post by madjo on 2007-10-19
How did you get it to run? I keep getting those latter two messages.

---

### Post by jrasmussen0 on 2007-10-19
I didn't have any problems, it just ran as icepodder.  You might need to undo any backported wxPython packages.  Make sure you downloaded the svn updates.  The packages available are the same old one I had installed under feisty.

---

### Post by madjo on 2007-10-19
Thanks that worked!

---

### Post by jonno on 2007-10-27
I can't get icepodder to run since upgrading to Gutsy.
Nothing happens when I try to launch from the app launcher and when I try from the terminal I get:
> [<class 'ipodder.players.XMMSPlayer'>, <class 'ipodder.players.NoPlayer'>]
Beep-Media-Player couldn't be imported
Traceback (most recent call last):
  File "CastPodderGui.py", line 3623, in <module>
    main()
  File "CastPodderGui.py", line 3592, in main
    config = Configuration(options)
  File "/usr/share/icepodder/ipodder/configuration.py", line 460, in __init__
    os.makedirs(self.download_dir)
  File "/usr/lib/python2.5/os.py", line 165, in makedirs
    makedirs(head, mode)
  File "/usr/lib/python2.5/os.py", line 165, in makedirs
    makedirs(head, mode)
  File "/usr/lib/python2.5/os.py", line 172, in makedirs
    mkdir(name, mode)
OSError: [Errno 13] Permission denied: '/media/AcomData-Maxtor320GB'


Any clues in this?

Jonno.

---

