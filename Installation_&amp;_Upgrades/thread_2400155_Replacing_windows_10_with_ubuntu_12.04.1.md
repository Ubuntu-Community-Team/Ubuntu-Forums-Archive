---
title: "Replacing windows 10 with ubuntu 12.04.1"
date: 2018-09-03
forum: Installation &amp; Upgrades
---

### Post by jehakega on 2018-09-03
I'm not able to replace Windows 10 with Ubuntu 12.04.1. The problem is that I don't see the window giving me the options to 'Install Ubuntu alongside Windows', 'Replace Windows with Ubuntu', and 'Something else'. The installer jumps directly to next window with a list of partitions and an the possibility to select device for boot loader installation, as if I had selected 'Someting else'. The list of partitions is however empty. When I press install in this window, an error message stating 'No root file system is defined. Please correct this from the partitioning menu' occurs.

Any suggestion on how to solve this?

---

### Post by jeremy31 on 2018-09-03
Try a different version of Ubuntu as 12.04 is EOL.  If the computer can run Win 10 it should be able to handle 16.04 or 18.04

---

### Post by jehakega on 2018-09-03
Thanks for the reply. Unfortunately, I need to install an application that only runs on version Ubuntu 12.04.1, so installing another version of Ubuntu is not an option. Is there any reason why an HP zBook 15 G4 should have any problem installing this old Ubuntu version?

---

### Post by jeremy31 on 2018-09-03
I don't think the Ubuntu 12.04 installer recognizes the file system used by Win 10.  It might be safer and easier to use virtualbox in Windows and install Ubuntu 12.04 in virtualbox

---

### Post by Topsiho on 2018-09-04
> **jehakega said:**
>  Is there any reason why an HP zBook 15 G4 should have any problem installing this old Ubuntu version?

There is. Ubuntu 12.04 is not supported, so installing this, on any computer, is not possible.
Using an obsolete OS, such as this version of Ubuntu, or Windows XP, **puts your computer at risk any time you are connected to the internet**. If you use your computer as a standalone, without internet connection, there is probably no problem, except that during the install no 12.04 files can be downloaded: no internet connection, and no extra 12.04 files available ...

Topsiho

---

