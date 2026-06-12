---
title: "create 10.04 usb boot for eeepc"
date: 2010-10-06
forum: Installation &amp; Upgrades
---

### Post by frazerr on 2010-10-06
Thanks for reading,

I have an eeepc with ubuntu 9.04 and i want to upgrade to 10.04

I also have a mac.  My eeepc does not have net access due to a bug in connecting to WPA networks.

I created a usb boot drive on my mac using the instructions on [http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download).  However my eeepc just ignore that at boot time.  And yes, I have made my usb the first boot option in the bios.

Once booted my eeepc can see the usb drive, so I dont know why it wont boot from it.

I thought perhaps I should make a boot drive from within ubuntu, on my eeepc, as one being created on a pc might work better than one created on a mac.

Is this the right thing to do?  Could someone please tell me how to proceed.  I have searched for a few hours and cant find how to do it.

9.04 does not have  'Startup Disk Creator'.  And my eeepc doesnt have net access.

Thanks for your help

---

### Post by C.S.Cameron on 2010-10-06
9.04 should have usb-creator, (in Terminal type "usb-creator").

---

### Post by MarkieB on 2010-10-06
no longer participating in ubuntuforums.org

---

### Post by frazerr on 2010-10-07
Hi guys.  Thanks for trying to help.  I dont know why I dont have usb-creator.

When I tried fdisk -l I got

WARNING: GPT (GUID  Partition Table) detected on sdc!  the util fdisk doesn't support GPT.  Use GNU Parted.

So I used parted.  deleted all partitions, and then ran
dd if=ubuntu.img of=/dev/sdc bs=1M

and it was still ignored when I tried to boot.

Any suggestions

---

### Post by srs5694 on 2010-10-07
Depending on the size of the ubuntu.img file and the size of the USB drive, it could be you've got GPT data structures left over at the end of the disk, and those may be causing problems. I recommend you use my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) to wipe the GPT data structures, then try again. You can use the Mac version, if that's more convenient for you. Do this:


[list=1]
[*]Launch gdisk on the disk. This would probably be "sudo gdisk /dev/sdc" in Linux or "sudo gdisk /dev/disk2" in OS X, but the disk device might be something else.
[*]Type "p" to review the disk's partitions. If it looks like you're editing the wrong disk, type "q" to exit and try another disk.
[*]Type "x" to enter the experts' mode.
[*]Type "z" to destroy ("zap") the GPT data structures. You'll be asked to confirm this; answer "y". You'll be asked whether to wipe the MBR; your answer is unimportant, given what you're about to do. The program should terminate.
[*]Try writing your image file again.
[/list]

---

### Post by frazerr on 2010-10-07
Hi,

I got gdisk, and then this error:


Problem opening /dev/disk2 for reading! Error is 16.
I couldnt find the error numbers on your site

help?

---

### Post by frazerr on 2010-10-07
ok, so I ejected the disk  (unmounted) and then got:

sudo gdisk /dev/disk2

GPT fdisk (gdisk) version 0.6.11

Problem opening /dev/disk2 for reading! Error is 2.
The specified file does not exist!

---

### Post by srs5694 on 2010-10-07
Were you running this on OS X? That's what uses the /dev/disk# device IDs. Use ls to view the available devices, as in "ls /dev/disk?". You'll have to figure out which disk device corresponds to the USB drive, but it'll probably be the highest-numbered one.

---

### Post by frazerr on 2010-10-07
yes, OS X

and I did check it was the right drive.  I wouldnt want to destroy all my other data.

---

### Post by srs5694 on 2010-10-08
The second error you reported, saying that the file does not exist, means just that: The file does not exist. Perhaps there was a typo on the filename...? All the error code numbers are those returned by the OS. I don't know offhand what error #16 is under OS X.

You could try using /dev/rdisk# rather than /dev/disk#.

Another option is to use a different utility, like OS X's GUI Disk Utility. Find the option to create a fresh partition table, but be sure to tell it to create a DOS/Windows/BIOS/Microsoft/MBR (whatever the term it uses is) partition table rather than a GUID Partition Table (I believe Disk Utility spells it out, rather than using the "GPT" abbreviation). It doesn't matter what partitions you create on it, since you'll be wiping them out when you write your image file.

---

