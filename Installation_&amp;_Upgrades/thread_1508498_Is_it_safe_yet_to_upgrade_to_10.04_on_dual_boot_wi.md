---
title: "Is it safe yet to upgrade to 10.04 on dual boot with Win7"
date: 2010-06-13
forum: Installation &amp; Upgrades
---

### Post by EvansFive on 2010-06-13
I have managed to successfully upgrade my iMac (dual boot Mac OS X and now Ubuntu 10.04) after resolving some initial problems with Grub.  I always like each Ubuntu release and 10.04 is excellent!  All my software has just worked and I had very little additional work to do after the upgrade.

I have a Dell PC that is dual boot Ubuntu 9.10 and Win 7.

I have seen a number of posts where people say after upgrading a PC to Ubuntu 10.04, Windows 7/XP etc no longer boots.  Somehow the boot loader gets clobbered,

If this is a bug has it been fixed yet, and therefore it is safe to perform the upgrade?

If the advice is no, then I will hold off a bit longer and just enjoy 10.04 on my iMac.

Thanks!

---

### Post by garvinrick4 on 2010-06-13
I have had no problems with Win7 dual booting with 9.10, 10.04 .10.10 or Fedora13.

They all work fine. Just in last page of install in Advanced tab put the grub in sda if installing on sda. Never sda1,sda5 just sda.
 If working with a drive sdb put grub in sdb not sdb1 or sdb5 just sdb. That is all there is to it really.

If you goof up your grub. It takes 3 or so small lines of code to put it back into sda.
 So know worries really.
Here is your code to go from karmic to lucid if you want to go from lucid to maverick anytime just change the names. Enjoy your Ubuntu
  	 	 	 	 	

sudo sed -i 's/karmic/lucid/g' [[COLOR=#3465a4]/etc/apt/sources.list[/COLOR]]("file:///etc/apt/sources.list") && sudo aptitude update && sudo aptitude dist-upgrade

---

### Post by EvansFive on 2010-06-13
Cheers thanks for that, I will go ahead and go the upgrade

---

### Post by darkod on 2010-06-13
The problem in those threads is this:
During the upgrade a windows will pop up asking where you want grub2 installed. Giving the user lots of option as always, ubuntu has decided to include in the list not just the disks device names (/dev/sda, /dev/sdb, /dev/sdc, etc), but also all partition names (/dev/sda1, /dev/sda2, etc).
The message in that window is slightly confusing, saying if you don't know on which disk your grub2 is, select all of them, because if you put it on a wrong one you won't see it boot right? But it says on all DISKS.
Unfortunately, it seems many people decide to handle the installation of their OS without even bothering to learn the difference between a partition and a disk. So they select all check boxes, including the partitions.
And because of the way windows boots, if you get grub2 installed in the boot sector of the windows partition, it won't boot.

In most cases even if you do this, it's easily fixable. But there have been situations where even the windows 7/vista/XP cd/dvd is not able to fix its own boot sector (not surprising).

Just make sure:

1. You know the way you dual boot, what is a disk, what a partition, and on the MBR of which disk is your grub.
2. Select only that disk MBR when asked.
3. Enjoy the upgraded system.

---

