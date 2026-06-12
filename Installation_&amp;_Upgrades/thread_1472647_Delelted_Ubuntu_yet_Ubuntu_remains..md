---
title: "Delelted Ubuntu yet Ubuntu remains."
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by rob22941 on 2010-05-04
I built up a pc and the primary os is Windows 7, I installed Ubuntu via wubi/inside the windows partition... I uninstalled/deleted Ubuntu yet Ubuntu remains on my boot menu. When I select Ubuntu it says:

\ubuntu\winboot\wubildr.mbr
[selected application is missing or corrupt]

I appreciate my windows pc confirming with me that I deleted something and then tell me it didn't follow through with my commands. 

How do I remove this listing of Ubuntu on my boot menu? I have an amd 64 bit cpu and a Nvidia motherboard. Not intel so steps if taken via start up will no be the same. Is this a Windows issue or Ubuntu issue? Thanks.

---

### Post by ajgreeny on 2010-05-04
In previous versions of windows you needed to edit out the ubuntu line from **C:\boot.ini**

I have not even seen windows7, never mind used it, but that may still be the answer.

---

### Post by Charlietje on 2010-05-04
you should rerwite your MBR. Depending on what windows you use, you need to boot with the windows CD en go to console

XP: FIXMBR
W7: bootsect.exe /nt60 C:

---

### Post by spydeyrch on 2010-05-04
I know of a more simple way, if you don't want to mess with the command line. Download and install EasyBCD. this will give you an option to add/remove options from your windows boot menu as well as reconstruct the MBR and the bootloader. It works like a pro!

-Spydey :KS

---

### Post by pedrogfrancisco on 2010-05-04
Er... His MBR is fine...

See here [Wubi Uninstall Ubuntu still in boot menu]("http://ubuntuforums.org/showthread.php?t=1086262")

You want the EasyBCD path, the last post from that thread is for Windows XP.

---

### Post by rob22941 on 2010-05-04
Found a solution through windows bcdedit.exe through cmd. Thanks anyway guys.

---

