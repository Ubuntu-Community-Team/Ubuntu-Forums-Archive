---
title: "Win2k + Ubuntu"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by XSAlliN on 2007-03-02
Hy, I want to install Ubuntu o a system were I already have installed win2k, I've seen on another topic some problems with Dual Boot of this two, could you point me the to the right steps, the data on Win2k is very important since is not mine and I'm not allowed to backup or do something to it, cause it's my brothers and I have the other half of the HDD, he could kill me if something happens to it, that's why I need your support on this (I'm serious - you mights say I'm playing with death). :( 

I have Ubuntu 6.06 LTS - if you're not sure I'll quit for now. [-o<

---

### Post by ajgreeny on 2007-03-02
It has never happened to me but there is no way that anyone can totally guarantee that there will be no loss of data on the windows partition that you will (I presume) be reducing in size to make room for Ubuntu.  If you really can't back up the windows files in some way acceptable to both yourself and your brother you need to think again I think.

However if the hard disk is already partitioned and Windows is on a separate partition to your half of the disk, then you can play around with your own partition without any real risk; as long as you don't touch your brother's partition, all his windows files will be safe.

If you give us more info about the current partitions and how they are set up, we can probably help you a bit more.

If you do decide to have a go with ubuntu it may be safer to get a new hard disk and add it to the machine, if your brother will allow you to and then try ubuntu on that.  Then his files will most certainly be safe, as long as you do nothing to the hda1 partition, where windows will be.

---

### Post by XSAlliN on 2007-03-02
C:\Win + D:\Bro stuff ....E:\Mine (free), partitioned in NTFS (as it was for Win), I was thinking of formating and go with Ubuntu, but will it overwrite the MBR like in the other case (a complaint on this forum related to Dual Bot 2K+ Ubuntu)?

Normally they should act separately, just fought I ask to know for sure :)

---

### Post by ajgreeny on 2007-03-03
Yes, ubuntu will overwrite the windows MBR and put grub there instead.  This may or may not be a problem as it could still be set to boot windows as the default, and you can even hide the grub menu if that will annoy anyone, using grub instead of windows MBR, but if you prefer not to do that, you could still install ubuntu using the alternate install CD, not the live CD, and choose to put grub on your own hard disk.  Then each time you want to boot into ubuntu you would need to change the boot order in the computer's bios.

If it were me, I would try to get permission to go ahead and put ubuntu's grub onto the MBR; it can always be removed and windows MBR restored if it is really a problem, and you can always restore grub to your own hard disk later if the MBR is restored

---

### Post by Arup on 2007-03-03
I have two drives, one with 2K and one with Ubuntu, I have tried out almost all major distros so each time they installed their own boot loaders, from SuSE to PC Linux to Fedora to Mandriva and now finally Ubuntu, that to after checking out Kubuntu and re-installed Ubuntu quite  a few times, not even once did I have trouble booting into Windows.

---

### Post by XSAlliN on 2007-03-03
It's just one HDD split in 3 Partitions, if there were to Drives It wouldn't be any problem.

---

