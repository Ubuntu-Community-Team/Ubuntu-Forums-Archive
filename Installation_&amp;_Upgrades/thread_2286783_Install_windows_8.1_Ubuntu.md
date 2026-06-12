---
title: "Install windows 8.1 Ubuntu?"
date: 2015-07-14
forum: Installation &amp; Upgrades
---

### Post by felipeg-117 on 2015-07-14
I currently have Ubuntu  14.04 LTS 64-bit installed on my computer there is no windows installation or any other OS dual booted at the moment. The thing that I want to do it create a 250 GB partition on my hard drive and install windows 8 on there for the single purpose of running a piece of software not compatible under wine and I don't want to do a Virtual Machine. I've looked onto various sites about this and most say that I will jave to install my GRUB again is this true? And if not can some one point me in the right direction as to how to do all of this?

EDIT: I realize the title mistake its supposed to be install windows 8 ON Ubuntu.

---

### Post by yancek on 2015-07-14
Windows historically has not booted other operating systems without manual intervention by the user so, yes you will need to reinstall Grub.  If you are using windows 8.1, you will first need to determine whether you are using UEFI/GPT to boot or the older MBR.  It makes a big difference.  I haven't installed windows for quite some time so I'm not sure if you can use unallocated space or if you should create an ntfs formatted partition prior to attempting to install.  You can do that with the Ubuntu install media using GParted.

---

### Post by felipeg-117 on 2015-07-14
> **yancek said:**
> Windows historically has not booted other operating systems without manual intervention by the user so, yes you will need to reinstall Grub.  If you are using windows 8.1, you will first need to determine whether you are using UEFI/GPT to boot or the older MBR.  It makes a big difference.  I haven't installed windows for quite some time so I'm not sure if you can use unallocated space or if you should create an ntfs formatted partition prior to attempting to install.  You can do that with the Ubuntu install media using GParted.
Non-Uefi and how do i reinstallgrub once i install windows

---

### Post by oldfred on 2015-07-14
Windows only installs to, repairs, or boots from a primary NTFS partition formatted NTFS with the boot flag. Default install uses two primary partitions, one a small Boot partition, but you can install to just one primary. Often best to be first primary. And a lot better if Windows primary is before an extended partition.

Back up partition table also after resizing for Windows, Windows does not correctly see Linux partitions and if a Linux partition is inside the extened it forgets to include it. So partition also has to be restored with testdisk or parted rescue.

You will need the live installer Ubuntu disk of the current version of Ubuntu you have. If you have upgraded, better to download same version as you are running.
       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by felipeg-117 on 2015-07-15
I got windows to install but every time I restart it automatically goes to Ubuntu how do I get to windows? Also doing all of this sparked up a problem with my wifi again it says its connected to the internet but refuses to go anywhere on browser or terminal or package manager What now? 

[http://ubuntuforums.org/archive/index.php/t-2256049.html](http://ubuntuforums.org/archive/index.php/t-2256049.html)

EDIT: Now my touch screen has stopped working too

---

### Post by oldfred on 2015-07-15
Each of those probably should be separate questions if you cannot find solutions in other threads in Forum.
Did you run this to find Windows?
sudo update-grub

But normally installing Windows will take over MBR and automatically boot. Or is system UEFI?

---

### Post by felipeg-117 on 2015-07-15
> **oldfred said:**
> Each of those probably should be separate questions if you cannot find solutions in other threads in Forum.
Did you run this to find Windows?
sudo update-grub

But normally installing Windows will take over MBR and automatically boot. Or is system UEFI?

I think Ubuntu just hit a rough patch or something wifi and toucscreen seem to be working fine now, the system is UEFI and trying the update-grub now

---

