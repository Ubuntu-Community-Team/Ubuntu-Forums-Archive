---
title: "Virtualbox Creation of swap space failed"
date: 2007-08-27
forum: Installation &amp; Upgrades
---

### Post by aprac00 on 2007-08-27
hello... I have tried to install Ubuntu 7.04 on virtual box and with 2 pc's! but an error keeps showing up "The creation of swap space in partition #5 of IDE1 master (hda) failed." someone recommended that I should change IDE1 to SCSI.. but I dont think this option exists in virutalbox
I have also tried using the alternative installing ISO however it didnt seem to boot up.. freezes with a black page and 2 lines at the bottom

---

### Post by aprac00 on 2007-08-28
from [http://forums.virtualbox.org/viewtopic.php?p=2973&sid=854707d4b4f39c9d401f1c9ce76b497b](http://forums.virtualbox.org/viewtopic.php?p=2973&sid=854707d4b4f39c9d401f1c9ce76b497b)


If you wanted a graphical solution :

1. Make a new hard drive (vdi) with VirtualBox.

2. Boot the Ubuntu desktop CD.

3. Run gparted as root :

Open a terminal and type :
Code:
gksudo gparted


4. Partition and format the virtual hard drive, which will be hda, with gparted. Make 1 partition for your root file system (where you will install Ubuntu) and your swap partition.

5. Then run the Ubuntu installer (aka ubiquity).

---

### Post by choward666 on 2007-12-21
had same issue....  instead of creating a fixed disk size using innotek virtualbox disk creator, I used "Dynamically Expanding" disk image and had no trouble.

---

### Post by Jaryth on 2008-02-13
I just have to back up what choward666 said. I was having the exact same issue, and switched it to "Dynamically Expanding" and it worked fine!
Running VirtualBox 1.5.4 on Windows XP SP3, trying to install Ubuntu 7.10 (all 32Bit)

---

