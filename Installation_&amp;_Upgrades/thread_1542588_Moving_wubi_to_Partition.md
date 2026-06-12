---
title: "Moving wubi to Partition"
date: 2010-07-30
forum: Installation &amp; Upgrades
---

### Post by homeero on 2010-07-30
hi, i've tried to install Ubuntu 9.04 last year but my modem was malfunctioning, so i gave up on Ubuntu, but i got a new modem and installed Ubuntu using wubi, i loved it and ill make it my main OS, but now i have 2 problems:
   1.-I tried using lvpm, but i ended up with a 60 GB new.disk and my hard drive has just 30 Gb (30 gb wubi installation and the 60gb from the new.disk) 
   2.-i dont know how to shrink windows partition and i dont want to loose my config, tweaks and installed apps
 my hard drive has 230 gb capacity and i want to leave at least 100 gb to windows

im sorry for any mistake and for my not-so-good English

-EDIT-
I decided to uninstal wubi and im going to install ubuntu the right way.. it just seems easier.. thank you

---

### Post by byStanderone on 2010-07-30
...i guess it would be of help to review lvpm, here's a thread bout it:

[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

---

### Post by oldfred on 2010-07-30
Check out these much newer instructions:

HOWTO: migrate wubi install to partition by bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Older instructions:
Old conversion LVPM, see Alternative Instructions 
[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)
1. Create 3 new partitions with the Partition Manager : a 10-20 GB (ext3 format) partition to use as root (/), a ~2 GB (equal to RAM size) (swap format) partition to use as swap, and make the rest a (ext3 format) partition to use as /home.
2. Boot back into the Wubi-generated Ubuntu install, mount the new partition that will be used as /home in the dedicated-partition install to /media/disk, and copy the contents of the current /home recursively over to the new partition:
rsync -avx /home/ /media/disk
Additionally, if you want to avoid the hassle of manually reinstalling all the packages you currently have installed, run:
dpkg --get-selections > selections.dpkg
That'll generate a list of packages you have installed (back up that list to somewhere safe); after reinstalling the system, just open Synaptic, go file > read markings, select that file that was generated (selections.dpkg), press apply, and it'll reinstall all the software you have on your current system ).

---

