---
title: "A litany of problems with GIS in 10.10"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by allenmaher on 2010-09-12
Since upgrading to the 10.10 beta I have had no end  of troubles getting the GIS software (GRASS GIS and QGIS) running.  In 10.04 this was almost flawless.  

Grass problems

The error message I get after installing all of the programs comes partway through initializing Grass with the wxpython gui, the project selection screen works fine, but one I hit the start grass button it craps out with the following message:

```
allen@Lisa:~$ grass
Cleaning up temporary files ...
Starting GRASS ...

          __________  ___   __________    _______________
         / ____/ __ \/   | / ___/ ___/   / ____/  _/ ___/
        / / __/ /_/ / /| | \__ \\_  \   / / __ / / \__ \ 
       / /_/ / _, _/ ___ |___/ /__/ /  / /_/ // / ___/ / 
       \____/_/ |_/_/  |_/____/____/   \____/___//____/  

Welcome to GRASS 6.4.0+42329 (2010) 
GRASS homepage:                          http://grass.osgeo.org/
This version running thru:               Bash Shell (/bin/bash)
Help is available with the command:      g.manual -i
See the licence terms with:              g.version -c
If required, restart the GUI with:       g.gui wxpython
When ready to quit enter:                exit

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

GRASS 6.4.0+42329 (SaskatchewanUTM):~ > Traceback (most recent call last):
  File "/usr/lib/grass64/etc/wxpython/wxgui.py", line 1818, in <module>
    sys.exit(main())
  File "/usr/lib/grass64/etc/wxpython/wxgui.py", line 1811, in main
    app = GMApp(workspaceFile)
  File "/usr/lib/grass64/etc/wxpython/wxgui.py", line 1736, in __init__
    wx.App.__init__(self, False)
  File "/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 7978, in __init__
    self._BootstrapApp()
  File "/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 7552, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
  File "/usr/lib/grass64/etc/wxpython/wxgui.py", line 1754, in OnInit
    workspace = self.workspaceFile)
  File "/usr/lib/grass64/etc/wxpython/wxgui.py", line 185, in __init__
    self.NewDisplay(show=False)
  File "/usr/lib/grass64/etc/wxpython/wxgui.py", line 1235, in NewDisplay
    auimgr=self._auimgr, showMapDisplay=show)
  File "/usr/lib/grass64/etc/wxpython/gui_modules/wxgui_utils.py", line 73, in __init__
    super(LayerTree, self).__init__(parent, id, pos, size, style=style, ctstyle=ctstyle)
  File "/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/lib/mixins/treemixin.py", line 488, in __init__
    super(DragAndDrop, self).__init__(*args, **kwargs)
TypeError: __init__() got an unexpected keyword argument 'ctstyle'

```

I can still start Grass with the tcltk gui (and a lot less functionality), but everything I have tried so far to rectify this (complete unistall and reinstall, etc...) has come to naught.

QGIS
Well the grass plugin does not work and the version is 1.4.0 which is a little dated, I can use [http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu](http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu) maverick  to get a later version which is OK and grass plugin works so all is not lost.

Anyone else have similar problems?

---

### Post by mörgæs on 2010-09-13
This forum might help you better:
[http://ubuntuforums.org/forumdisplay.php?f=385](http://ubuntuforums.org/forumdisplay.php?f=385)

---

### Post by allenmaher on 2010-09-13
Thanks I will repost there.

---

### Post by Iowan on 2010-09-13
Topic moved to:
 [http://ubuntuforums.org/showthread.php?t=1573701]("http://ubuntuforums.org/showthread.php?t=1573701")

---

