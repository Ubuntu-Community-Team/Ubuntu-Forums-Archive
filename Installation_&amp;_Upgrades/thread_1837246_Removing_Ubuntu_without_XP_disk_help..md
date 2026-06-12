---
title: "Removing Ubuntu without XP disk help."
date: 2011-09-01
forum: Installation &amp; Upgrades
---

### Post by wibbid on 2011-09-01
Dear all

Aplogies if this has been posted before but I have been searching EVERYWHERE for hours on the net how to do one probably simple thing:

Remove Ubuntu which is currently dual boothing alongside XP from a separate partition WIHOUT a windows disk.  This is because my laptop is an old Samsung NC-10 and never came wih any disks.  I have been scouring everywhere but still dont understand about Grubs etc... part of the reason why I'm trying to get out of the Linux world as I really don't understand much of it!  I tried just removing it from the partition but obviously got the grub error after restarting so was forced into reinstalling Ubuntu.

Please any beginners language help would be greatly appreciated!  I have tried using some free software out on the net but don't understand how it works....

---

### Post by coffeecat on 2011-09-01
You need to re-install the Windows bootloader to the mbr for which normally you would need to run fixmbr from a Windows XP CD. Fortunately, you can install code which has the same functionality from an Ubuntu live CD. Have a look here:

[http://ubuntuforums.org/showpost.php?p=8950739&postcount=7](http://ubuntuforums.org/showpost.php?p=8950739&postcount=7)

That describes three different methods. Most people find the first, using lilo, to be quite satisfactory. You need to be connected to the internet when you do this so that the package manager can download the necessary packages. Before you quit the live session, open Gparted and make sure your Windows partition has the boot flag set. It cannot boot without the boot flag. You can also use Gparted to reformat the old Ubuntu partitions so that you can use them in Windows.

---

