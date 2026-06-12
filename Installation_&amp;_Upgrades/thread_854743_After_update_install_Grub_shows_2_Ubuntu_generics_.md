---
title: "After update install Grub shows 2 Ubuntu generics and 2 ubuntu generic recovery modes"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by Universal344 on 2008-07-09
Hi,

I recently installed an array of updates that were available from the update manager.  After installing them Ubuntu told me I had to reboot.  So, I clicked reboot now.  When Grub loaded Ubuntu generic was first in the list as normal and I pressed enter.  But, after it finished loading my screen went black and my monitor indicated it was not receiving a signal.  After waiting a while I rebooted and looked more closely at Grub.  First in the list was Ubuntu generic then Ubuntu generic recovery mode then Ubuntu generic and Ubuntu generic recovery mode again which were followed by the usual entries.  I tried loading the second Ubuntu generic and it booted fine.  Can anyone tell me how to safely remove the first two entries of Ubuntu generic and Ubuntu generic recovery mode?:confused:  

Please note:
-I am still using distro 7 gutsy gibbon (havent gotten around to upgrading but was going to in the next few days).
-I am also running Windows Vista on my machine.
-I have installed many updates in the past and this has never happened.

P.S. please pardon my spelling

Any help is greatly appreciated.

---

### Post by Activist on 2008-07-09
terminal ->
> sudo gedit /boot/grub/menu.lst

remove the double ones... but before make sure the double entries are exactly the same

---

### Post by Universal344 on 2008-07-09
I took a look at the file and the top two listings (the top one didn't work, screen went black) were Ubuntu kernel 2.6.22-15-generic
and the bottom two were Ubuntu kernel 2.6.22-14-generic

---

### Post by Universal344 on 2008-07-10
bump

---

### Post by matthewbpt on 2008-07-10
I get two kernels listed in my boot too since i updated but they both work so i cant imagine why yours doesnt, but anyways since they dont, boot into the old one instead, and then remove the new kernel with the package manager

---

### Post by SkonesMickLoud on 2008-07-10
Search Synaptic for the kernel that is not working, mark it for deletion, and click apply.

---

