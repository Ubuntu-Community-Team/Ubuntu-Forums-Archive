---
title: "Converting GRUB back to NTLDR"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by schafferm on 2007-05-04
Hi 

For various reasons I want to convert my GRUB loader back to NTLDR.  Any suggestions on how to do this without trashing my XP-Pro and Ubuntu installations?

Michael

---

### Post by dannyboy79 on 2007-05-04
> **schafferm said:**
> Hi 

For various reasons I want to convert my GRUB loader back to NTLDR.  Any suggestions on how to do this without trashing my XP-Pro and Ubuntu installations?

Michael


very easy, simply boot using your windows xp install cd, go into the recovery console, chose your Windows Install and at the password prompt enter your passowrd otherwise blank, chose to repair it manually, then at the command prompt,  FIXMBR.

type FIXMBR [device name]

where device name is the nomenclature the Recovery Console’s MAP command uses to describe the various hardware devices in your computer. For example, you might type FIXMBR\device\HardDisk0 to restore your boot record’s MBR. If you don’t enter a device name, FIXMBR repairs the MBR of the default system disk. 

BEFORE YOU DO THIS, JUST AS A PRECAUTIONARY MEASURE, USE LINUX TO BACKUP THE FIRST 512 bytes OF YOUR DISK, which is your MBR along with the Partition table. you would do this with this command:
(NOTE: this is assuming you want to backup the MBR along with the Partition Table of your first hard drive (hda) and you'll be storing (saving it) into your users home dir and naming it MBR.img

sudo dd if=/dev/hda of=/home/usernamehere/MBR.img bs=512 count=1

and then if something goes wrong, restore it by booting into a live cd, mount the hard drive somewhere that contains the image and use this command:
(NOTE: this is assuming you want to restore the MBR along with the Partition Table of your first hard drive (hda) and you'll be restoring (saving it) into your users home dir and naming it MBR.img

sudo dd if=/whereeveryoustoredit/MBR.img of=/dev/hda bs=512 count=1

if you didn't want to backup the partition table along with the first 446 bytes of the hard drive, you would just use 446 instead of the 512 that I put in the command. (all this info is thanks to Herman, here is the link to backing up your MBR: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)) Herman is the man when it comes to Grub and dual booting.


Anyway, after you ahve backed up your mbr JUST IN CASE, then perform the FIXMBR and you should be able to boot right into Winbloz. then you can even add a Ubuntu boot option within NTLDR if you'd like so you can still dual boot but using NTLDR instead. Those instructions are here: [http://jaeger.morpheus.net/linux/ntldr.php](http://jaeger.morpheus.net/linux/ntldr.php)

---

### Post by schafferm on 2007-05-04
Wow =)

Thank You for the very detailed answer!!!!!!

Michael:KS

---

