---
title: "Install fails at software packages - 2 different cds"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by jdforsythe on 2007-05-16
I downloaded Ubuntu Studio from the torrent, checked the MD5, everything is okay.

I burnt the ISO to a dvd, reset, and installed.  First time through it locked up because I had my ipod plugged in.

Once I figured that out and tried again, it got through all the setup, the partitioning, and through installing the base system.  It brings up the selection box for audio, video, graphics, plugins.  No matter what I choose to install (even if I choose nothing) it errors out during the software install (after about 2 seconds it gives me the red screen and won't install the software).  I can install grub and "finish installation" just fine, so I tried booting up just like that, figuring that I would just have to install those packages afterward.

However, it now only boots to a command prompt.

I checked the CD integrity and it fails within a second on a file called "python" something or other.

So I booted back up into XP, rechecked the md5 of the iso, just fine.  Burnt to a new disc, this time at the slowest possible speed.  I get the same failure on checking the disc, and it fails in the same place when picking software and installing.

I know the file can't be corrupt, because the hash checks out.  I'm using Alcohol 120% to burn the ISO (I tried using Nero, but it thinks the iso is a cd - errors when you put a dvd in - but also errors on inserting a cd because it's not large enough to hold the iso!).

So I need to know if there is a better tool to burn the image to disc so it doesn't corrupt, or if someone else is having this error and has a way to fix it.

Also, in the meantime, I'd like to know how to get into the GUI desktop from the command prompt.

I'm dual-booting XP and Ubuntu Studio (just until I can convince my wife to make the switch completely, then XP is history).
I have a 20GB drive:
0,1 is ext2 mounted on /
0,2 is swap
0,0 is ntfs (xp install)

and a 320gb drive for data
1,0 ntfs

Thanks.

---

### Post by gwoodard on 2007-05-16
Hey try CDBurnerXP Pro 3 (Download.com) after installed go to burn data/iso to file to Burn ISO from file then open the iso (make sure you burn it at 4x other wise it will not work) don't worry it can burn dvds as well

---

### Post by cetheriel on 2007-05-16
shouldn't there be a way to copy the files to hard disk, then boot and install from hard disk?

---

### Post by gwoodard on 2007-05-16
Sorry it isn't that simple you either can upgrade or install from cd or dvd:(

---

