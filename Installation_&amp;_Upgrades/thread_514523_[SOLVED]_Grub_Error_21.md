---
title: "[SOLVED] Grub Error 21"
date: 2007-07-31
forum: Installation &amp; Upgrades
---

### Post by Troubled on 2007-07-31
EDIT: The title of this thread should actually be "Grub Error 22".

**The Goal:** Deleting one of my partitions

**The Problem: **GRUB loads from that partition

**The Background:**
On my laptop there are currently four partitions:
one, the default windows install
two, the factory-installed backup partition
three, the latest version of ubuntu (which I like very much and want to keep)
four, the 6.06 LTS version of ubuntu (which I installed for some troubleshooting and don't want to keep)

So, I wanted to get rid of this fourth partition to free up some space for my main ubuntu OS. I asked around in #ubuntu on IRC and was directed to the gparted utility, which I happily used to wipe my fourth partition (which was installed AFTER the one with the latest version) and increase the space on my third partition.

When I booted up my computer again, I received GRUB error 22: "What the **** happened to my partition?"

Fortunately I had the 6.06 live cd ready, which I used to reinstall that OS on some free space that I had left, and my computer booted fine (through the GRUB on the 6.06 install).

But this brings me back to square one: how do I get rid of an ubuntu install (or any install, for that matter) if it's the one that boots up my OS's?

My older installs only recognize the presence of the OS's present on the system at that time, ie, windows recognizes itself, the current ubuntu recognizes itself and windows, and 6.06 recognizes itself, the other ubuntu, and windows as well.

Any help is appreciated! Thanks.

--John

---

### Post by MQMike on 2007-07-31
Should not be a problem -- many of us do that all the time while experimenting.

Re-install GRUB to the Master Boot Record of your hard drive, this time using the Ubuntu on partition 3 “the latest version of ubuntu (which I like very much and want to keep)”

First, you need to get a grub prompt (grub>).
Put your Live CD in the CD tray, re-boot your PC, startup your Live Kubuntu.  
Now get a terminal and proceed as follows:

Get a GRUB prompt as root by typing 
sudo grub  (then press Enter), 
and type the following (press Enter after each command):

grub>  root (hd0, 2)          # (hd0,2) is the partition of your "main" favorite Ubuntu
grub>  setup (hd0)          # This assumes (hd0) is your “main” booting hard drive MBR
grub>  quit
$ exit

Close out all windows.
Re-boot to test it.

- - - - -

Edit the boot menu (/boot/grub/menu.lst)?

After doing all this, you * may * (but maybe not, too!)  still have to edit the boot menu for GRUB, which is contained in Ubuntu at /boot/grub/menu.lst.  (.lst is an “l” as in “list.”)
You must edit it as root, and don’t forget to save your changes when you are done (File-Save, File-Quit).

The part you need to check/edit is the boot menu for Windows, which should look like:

title Windows XP or whatever you wish to call it
rootnoverify (hd0, 0)
makeactive
chainloader +1

where:
(hd0, 0) is your Windows partition.
(GRUB, the bootloader starts counting from zero.  So hd0 is the first hard drive, hd1 is the second hard drive, etc.;  the first partition is partition 0, the second partition is partition 1, etc.)


For all the details:
How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)


THEN you can use GParted to delete your 4th partition, or you can do it before doing the above.

---

### Post by Troubled on 2007-08-04
Thank you, your solution worked perfectly!

---

### Post by MQMike on 2007-08-04
Troubled -- That's Great!  Thanks for your feedback that you got it to go just right!  :)

---

