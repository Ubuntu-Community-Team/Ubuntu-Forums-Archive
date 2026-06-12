---
title: "[SOLVED] Installing Xbuntu and partitioning"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by carterrocks on 2008-01-03
Okay my original idea was to install Ubuntu because of its  built-in dual booting.  But to cut a long story short I now want to install Xbuntu.  I have the live CD, all happy until i realised the installation is different.  I kinda memorised the installation process for UBUNTU, since i'm really paranoid about losing XP.  So anyway in Xbuntu the  installation doesn't give you the same option wen partitioning, ubuntu says something about free space?
Anyway how can i have both Xbuntu and Xp (which is already installed) on my PC?  WIll i need to download extra software?

---

### Post by jan quark on 2008-01-04
for dual booting check out this guide
[HTML]http://apcmag.com/node/5162/[/HTML]

---

### Post by perixx on 2008-01-04
**Firstly recommended: backup your personal data on XP!!**
If you like to shrink your current XP-partition for the sake of making room for Xubuntu, you should read the info I wrote here (last post on the page):
[http://ubuntuforums.org/showthread.php?t=656363&page=3]("http://ubuntuforums.org/showthread.php?t=656363&page=3")

You then might use the (**first option**) automatic setup  (splitting up availible HDD space 1/1 for XP and Ubuntu) or - and only that (!) - the **MANUAL** installation where you specify yourself, where you want to place the Ubuntu-installation (know what you're doing!) - most especially, don't choose the XP-partition for installation (of course :]) and be prepared for trouble when installing the Grub bootloader into the Master Boot Record (MBR=on hd0)!
This might also apply to using the automatic setup (!)

In case you want to be on the save side regarding partitioning and resizing, use 'gparted' from your live-CD and manual installation (installing Grub to the Xubuntu partition's superblock - e.g. (hd0,1), not the MBR!) or the first option from above in the first place.

Be careful **not to** choose the 'use all of HDD' - then, Ubuntu would delete your XP partition beyond recoverability!! 

Secondly, if you're really in fear of corrupting your XP installation, you could use the nt-bootloader (already in MBR) for chainloading your Grub-bootloader in the Xubuntu partition's superblock. This way, the MBR is **NEVER** touched, therefore, XP-booting can hardly be affected. If you're interested in this method, look here (first, edited post):
[http://ubuntuforums.org/showthread.php?t=621827]("http://ubuntuforums.org/showthread.php?t=621827") 
or here
[http://ubuntuforums.org/showpost.php?p=1229036&postcount=9]("http://ubuntuforums.org/showpost.php?p=1229036&postcount=9")

perixx

---

