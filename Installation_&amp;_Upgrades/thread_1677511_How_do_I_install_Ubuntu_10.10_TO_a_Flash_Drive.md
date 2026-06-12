---
title: "How do I install Ubuntu 10.10 TO a Flash Drive?"
date: 2011-01-28
forum: Installation &amp; Upgrades
---

### Post by boopit on 2011-01-28
Is there any way I can install Ubuntu to my flash drive so that all of my settings and files are saved on my flash drive?

I like the idea of carrying around my whole OS and filesystem on a keychain.

Thanks in advance.

---

### Post by andymorton on 2011-01-28
Hi, 

I've copied and pasted the following from this website - [http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

I hope it helps
andy :)


Backing Up Whole Installations

Remastersys makes a custom live/installer CD image out of your existing installation. You have the option to do so just for your system files or for also your personal preferences... or your entire installation (of course, if you have a lot of personal files, the CD or DVD image might be too big to be useful. Instructions here on how to use it.

PartImage is a nice little program that creates an image of your entire partition. You'll need a live CD for this, and you can find more details here about how to use it.

tar is an archiving command, but it can also be used to archive your entire system into one little zipped up bundle. Someone on the Ubuntu Forums wrote a nice little HowTo on backing up and restoring your entire installation using tar.

ddrescue allows you to copy a partition byte for byte to another partition or to a .img file. It's mainly designed for recovery of a crashed drive, but you can also use it as a way to back up (a non-graphical PartImage of sorts). The trick is that the name of the package is ddrescue in the repositories, but the command to use it is dd_rescue. So if you wanted to copy /dev/hda1 to /dev/sda1, you would type in the terminal:

dd_rescue /dev/hda1 /dev/sda1
Keep in mind that /dev/hda1 cannot be in use or mounted. If that requires you using a live CD, then so be it. You can also, if you don't want to erase /dev/sda1 completely, ddrescue to an image file and then mount the image to get the files off it:
dd_rescue /dev/hda1 /dev/sda1/hda1backup.img
sudo mkdir /recovery sudo mount /dev/sda1/hda1backup.img /recovery

---

### Post by oldfred on 2011-01-28
You should have at least a 8GB flash drive, but it can be installed in 4GB but you will be constantly housecleaning and cannot load very much additional software.

Grub will default to installing to the sda MBR, you have to use manual partitioning and choose where to install the boot loader.

It does not have to be encrypted:
Standard full install to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")
More discussion Dec 2010
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs  or run fsck. But if partition is small then it does not take long to  fsck anyway and without journal writing is reduced.

Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

See post #19 C.S.Cameron - recommends disconnection sda so grub can only install to flash drive.
Maverick now only gives combo box on grub location if you use manual install.
Lucid:
[http://ubuntuforums.org/showthread.php?t=1509603](http://ubuntuforums.org/showthread.php?t=1509603)

---

