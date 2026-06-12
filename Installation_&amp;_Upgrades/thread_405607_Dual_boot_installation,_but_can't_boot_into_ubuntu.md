---
title: "Dual boot installation, but can't boot into ubuntu"
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by Divad89 on 2007-04-10
I've just installed Ubuntu from the Live-CD, and done it just like I saw on a homepage, but when I restart after the installation I don't get the opportunity to boot into Ubuntu, it just "auto" boot into the existing Windows XP installation, do you know what I've done wrong, and how I can boot into the Ubuntu installation?

Sincerely
David

---

### Post by jobox on 2007-04-10
Well, I might.
From the sounds of it you are booting the windows partition directly, instead of the grub boot loader. What you need to do to fix this is configure your BIOS to boot of the partition/mbr (or disk if you prefer) that ubuntu was told to install grub on. If you don't remember you can try to boot of all of them sequentially until you get a grub message and a menu. This menu should hold options for atleast 1 ubuntu linux kernel and the windows os you have installed.
If it doesn't you'll need to keep booting from this partition, but reconfigure grub before it will work.

If you want a fool-proof method boot of your live cd and examine the /etc/fstab. Find the  partition associated with the mount point /boot and thats where you grub-config will be. Exact location is /boot/grub/menu.lst, now the grub itself can be installed to a new location by invocing sudo grub-install <partition> where partition can be for instance hda. then configure you bios to boot from this device (hda). If you need to confirm what hardware this device is you can do so by checking out what ide or scsi contact the cables are connected to. hda is ide master 1 sda is scsi master 1

---

### Post by dbrjay on 2007-04-10
if you download the GRUB manual first and follow the steps to make a boot disk. Set your BIOS to boot from disk and test the boot disk works 100% before transfering GRUB to your MBR (steps to do this are also in the GRUB manual). 
NB. GRUB partition notation is different from LINUX partition notation.

---

### Post by Divad89 on 2007-04-10
But I don't understand it, in bios you can't decide what partition you'll boot up on first, what I know you can only decide what harddrive you'll boot up on first, but I have Windows and Ubuntu on the same harddrive. How can I fix it then?

Sincerely
David

---

### Post by dbrjay on 2007-04-10
download GRUB and the manual. Using the ubuntu installation disk boot into ubuntu and make a GRUB boot disk (follow the GRUB documentation) or just do a google search, there is plenty out there.. 
once you have created the GRUB boot disk change BIOS to boot from floppy first, this will bring up the boot menu stored on the floppy. Ensure that the boot floppy works,  if it does not enter the command line by pressing 'c'  or edit the commands to call the boot loader from by pushing 'e'.. once you have the dual boot working on the floppy, make a backup of it somewhere and then upload GRUB to the MBR on the HDD. See documentation.

NB. In documentation the file 'grub.conf' is reffered to, ignore this file and instead use 'grub.list' ... its the same file. Grub.conf is not required. 
PS. I have a tri-boot machine and it works fine with GRUB.

---

### Post by neilengineer on 2007-04-10
Try to press "up" OR "down" key all the time on your keyboard when you power on your PC.  And see what happens.   If there appears a menu with OSes, just choose Ubuntu.

---

### Post by dbrjay on 2007-04-11
[QUOTE=neilengineer;2433435]Try to press "up" OR "down" key all the time on your keyboard when you power on your PC.  And see what happens.   If there appears a menu with OSes, just choose Ubuntu.[/QUOTE

you are reffering to the GRUB or LILO boot menu. Configuring these will give a list of different OS's.

---

