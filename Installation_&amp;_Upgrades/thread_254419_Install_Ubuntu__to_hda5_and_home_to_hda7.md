---
title: "Install Ubuntu / to hda5 and /home to hda7 ??"
date: 2006-09-09
forum: Installation &amp; Upgrades
---

### Post by lagagnon on 2006-09-09
I want to install Ubuntu Dapper Drake to two partitions: hda5 and hda7. I would like to install "/" to hda5 and "/home" to hda7. Is this possible using the graphical installer from the Live CD?? because I am unable to find any such options or maybe I'm missing something?

Any help greatly appreciated.

---

### Post by lukew on 2006-09-11
Hay,

Yes it is, you have to go through the advanced options.

Luke

---

### Post by tsiMental on 2006-09-11
This is easily done after you've installed your ubuntu system by using a terminal:

Edit your /etc/fstab to include a mountpoint for hda7 in /home - look at the other mountpoints to know how. (gksudo gedit /etc/fstab)

then type:
sudo mkdir /backup
sudo cp -rp /home /backup
sudo mount -a
sudo cp -rp /backup/home/* /home/*

If something goes wrong, just remove the line for mounting hda7 in /home from your /etc/fstab and type 'sudo mount -a' and find the error.

Edit: Please note that your hda7 partition needs to be formatted using a linux compatible filesystem before you do this (not FAT, NTFS or HPFS) - ext3 is good.

---

