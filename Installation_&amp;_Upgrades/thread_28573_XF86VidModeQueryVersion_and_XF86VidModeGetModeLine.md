---
title: "XF86VidModeQueryVersion and XF86VidModeGetModeLine"
date: 2005-04-20
forum: Installation &amp; Upgrades
---

### Post by chpts on 2005-04-20
Hi everyone, I'm trying to install the "visualization toolkit" (VTK), but towards the end of the compilation process (I know is near the end because I've installed VTK from CVS a few times before in other distros) it says: libvtkRendering.so: undefined reference to `XF86VidModeQueryVersion'
And: libvtkRendering.so: undefined reference to `XF86VidModeGetModeLine'

I didnt want to post without doing some research, basically I found posts complaining about the installation of Mplayer with the same error report. So I proceeded to do what they recommended: 

sudo apt-get install xlibs-dev libxinerama-dev libxss-dev libxxf86vm-dev libxxf86misc-dev

and :  sudo apt-get install x-window-system-dev

but I still got the same errors.

Any Ideas?

Thanks in advance.

Juan

---

### Post by chpts on 2005-04-24
Finally I managed to make it work, I just needed to set the variable: 

and that was it, no more errors.

Look in [http://www.vtk.org/Bug/bug.php?op=show&bugid=1777&pos=0](http://www.vtk.org/Bug/bug.php?op=show&bugid=1777&pos=0) for more information.

---

