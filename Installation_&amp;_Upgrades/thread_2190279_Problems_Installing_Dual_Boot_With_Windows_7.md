---
title: "Problems Installing Dual Boot With Windows 7"
date: 2013-11-26
forum: Installation &amp; Upgrades
---

### Post by artillery on 2013-11-26
Hi. I am having problems with installing Ubuntu to dual boot on my PC whith Windows 7. I am running Windows 7 Home Premium 64 bit on a 2 TB Samsung HD. When I try to install Ubuntu from CD the installer recognizes I have Win 7 running on a 2 TB HD and it gives me the option to do a full install overwriting Windows 7 but not to install alongside Windows 7 . I also get the "Other" option allowing me to re-size partitions.
I have also tried install discs from other Ubuntu based distros (Mint, Zorin) and get the same choices with no dual boot option.
I'm trying to install Ubuntu 64bit BTW. ATM the HD is NOT partitioned in any way.
Any help to get round this would be greatly appreciated. It.s been a while since I played around with this kind of issue so the old acronym KISS (Keep It Simple Stupid) comes to mind. as I am not feeling very clever ATM  ;)

---

### Post by oldfred on 2013-11-26
Have you used all 4 primary partitions. That is very common with Windows 7 installs as it also has a hidden (in Windows) 100MB boot/repair partition.

Post this from terminal.
sudo parted -l

If you have all 4 used, you will have to delete one. Never create partitions with Windows as it may convert to dynamic which does not work with Linux (and some Windows repair tools).

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by artillery on 2013-11-27
Sorted. Thanks for the heads up about the max partitions issue. Nice to know.
As it happens it was something far more straight forward, I only had two partitions on the HD. So after digging around thinking great technical thoughts I right clicked on a partition and on reading all the properties text saw it stated I had a problem with the NTFS structure and needed to run chkdsk.
Ran chkdsk and sorted. 
Nothing like doing the bleeding obvious is there ??? (Rolls eyes and bangs head off desk)

---

