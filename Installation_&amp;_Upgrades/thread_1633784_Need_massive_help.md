---
title: "Need massive help"
date: 2010-11-29
forum: Installation &amp; Upgrades
---

### Post by elsneakums on 2010-11-29
So i got a new pc and decided to put 10.10 on it, used it for about a week then today the software center stopped working so i decided to put 10.04 on it as that worked fine on my old pc. I went through the motions on installing it and it insists on formatting the drive with ext4 (my old pc on 10.04 was ext3) if i proceed i get this message Process 305 glib warning getpwuid_(c):failed due to unknown user id. I can not install winowz as it throws up an error, ive tried p.magic 3.0 live cd to try and fix this but everytime i try to install ubuntu no matter what version (tried 9.10 also) i get the same wanting to format drive as ext4 then the 305 error. If anyone can help i will be gratefull, would have puled my hair out if i had any!

---

### Post by leclerc65 on 2010-11-29
I usually use Gparted live CD to prepare the partitions. While shutting down Gparted will pop the CD, replace it with the Ubuntu CD then start the installation.

---

### Post by elsneakums on 2010-11-29
Tried that to partition the drive, as soon as i click apply gparted live screen goes black and the caps lock and scroll lock lights on my keyboard start flashing on and off at the same time. Is this fixable? is it a bios problem as to why ubuntu is trying to install ext4 all the time?

---

### Post by akand074 on 2010-11-29
Is this through manual installation? I can understand if the auto installer tries to do that but I've installed using many file systems in versions 10.04 including EXT3, EXT4, Reiser FS, btrfs.. I use EXT4 currently, I still find it the best at the moment. There shouldn't be an issue if you use the "manual install" method assuming you know how to install from there. If you wanted to install Windows after you could always use the Windows disk to partition the drive to fit Windows. But other than that its likely hardware issue because I don't think that has anything to do with Ubuntu/software if you can't get it working.

---

### Post by pricetech on 2010-11-29
I've never had any issues with partitions either.  I usually just let the installer partition for me, though I do run gparted from the live CD to remove any existing partitions first.

Don't really think it's your BIOS, but a reset to defaults wouldn't hurt.  You might also check to see if there's an upgrade.

---

### Post by elsneakums on 2010-12-01
Thank you all, manual install worked a treat :D

---

