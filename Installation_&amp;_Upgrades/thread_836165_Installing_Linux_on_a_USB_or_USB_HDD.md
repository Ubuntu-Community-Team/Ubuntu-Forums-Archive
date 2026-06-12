---
title: "Installing Linux on a USB or USB HDD"
date: 2008-06-21
forum: Installation &amp; Upgrades
---

### Post by Albinoni on 2008-06-21
Hi I'm a newby here and also a newby to Linux. I have been a Windows user most of my life and have played with Linux before but not often, more so like a trial thing.

Ok this is what I'm planning to do.  I've got Linux Ubuntu 8.04 on a DVD which came with a PC Magazine here in Australia.  What I would like to do is to either in stall it on a 4GB USB flash memory stick or a 40GB USB external HDD and would like to know if this possible.  I know my laptop (Toshiba P200 Satellite) does support boot from USB device so there should not be a problem there, though I'm not sure if it supports installation to USB Device and this option will come up on the installation screen when it comes to installing the software/OS.  I'm sure it would.

I dont want to run Ubuntu off my laptop HDD but like I said boot off either a 4GB USB stick or better still an external 40GB HDD.

Also how much free space is required for Ubuntu 8.04 is 4GB flash drive enough ?

If I install it on a USB HDD, do I need to make a small partition on the USB HDD ?

Thank you.

---

### Post by Pumalite on 2008-06-21
You can install 8.04 from the installation CD treating it as any Hard Drive. Find out your USB with:
sudo fdisk -lu
During installation; at step 7 or 8; go to 'Advanced Tab' and change (hd0) for /dev/???; where ??? is your USB as given by sudo fdisk.
[http://ubuntuforums.org/showthread.php?t=789528](http://ubuntuforums.org/showthread.php?t=789528)
4 GB is probably enough. 8 would be better

---

### Post by shakyone on 2008-06-21
I would also disconnect your hard drive in the computer before you start.  That is what I did to preserve the files and mbr.  You don't have too, but I would, and did.  And I have done this 11 times now since 2006.  

Some suggestions, use the disk manager function of Windows to delete all the partitions on your USB drive, so you have an unformatted USB thumb drive/hdd.  It really simplifies things, and you don't need to do the steps mentioned earlier.  

When you enter gnome, you may see the USB drive present, just right click and unmount it.  There used to be a set of buttons to select/deselect how Ubuntu mounts "external drives and media" but this was removed in 8.04.

Proceed with the normal installation with the internal drive removed, and when you get to the select the hard drive portion, if you removed the internal HDD, the thumb drive should be the only one drive shown.  Its size should match.  Just proceed as normal.

I use a USB HDD, and look forward to trying with a thumb drive.  I am guessing it will run a little quicker.

---

### Post by Pumalite on 2008-06-21
Better use Gparted from the Live CD. You have to boot it after all. (Partition Editor). I have installed without disconnecting the internal drives, ever, but is an added measure of security for someone new to the process.

---

### Post by Albinoni on 2008-06-21
Two Q's here:

1. I was told on another Forum that it's much easier to install Linux on a USB External HDD than a USB Thumb drive and during the
installation process it will ask me where I would like to install the OS eg C, D F etc, obviously I'd choose the USB External HDD.

If I run the CD as live i.e try it out, how do I get out of it and go back into Windows ?  Do I just simply eject the CD and re-boot the PC back into Windows?

---

