---
title: "VirtualBox 4.0.4 &amp; QGIS 1.4 not starting in windows interface - libQt* issue?"
date: 2011-03-25
forum: Installation &amp; Upgrades
---

### Post by paulysa1969 on 2011-03-25
I run VB 4.0.4-70112 under Ubuntu 10.10 which stopped working after I installed Google Earth 6 using these instructions: [http://ubuntuforums.org/showthread.php?t=1666337](http://ubuntuforums.org/showthread.php?t=1666337)
;)

VirtualBox wont start under the windows interface but when I issue this command at the comand line in a terminal::(

VirtualBox

I get this error:

VirtualBox: supR3HardenedMainGetTrustedMain: dlopen("/usr/lib/virtualbox/VirtualBox.so",) failed: /usr/lib/libQtOpenGL.so.4: undefined symbol: _ZN14QWidgetPrivate15checkWindowRoleEv

I also run QGIS version 1.4 also not starting in the windows interface:(.

When I open a terminal and issue the command to start QGIS in windows like this:

pauly@PaulSamsungNC10:~$ /usr/bin/qgis %F


I get this error:

/usr/bin/qgis: symbol lookup error: /usr/lib/libQtSvg.so.4: undefined symbol: _ZN14QObjectPrivate15checkWindowRoleEv



Could this be a libQt* issue.:???:

Has anyone had this issue and can anyone offer some input.

Thanks

---

