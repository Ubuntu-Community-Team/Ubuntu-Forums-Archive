---
title: "ubdating to edgy eft from dapper drake"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by thinman1189 on 2007-05-04
Well I updated today and had a few problems. I was getting an error about a repository not responding so I searched around and turned off some that I thought were unnecessary. I retried and it work.

After the installation I was prompted to restart and clicked okay. My computer restarted as normal: Acronis popped up and I chose Ubuntu instead of Windows(They're stored on two separate drives). 

A loading screen popped up. It had the same logo as before but didn't show the processes and the loading bar was segmented. I assumed this is the default in the new version.

After the bar filled up the screen went blank. Here's the twist, if I hit Control + Alt + Del and then enter the computer restarts. If memory serves correct that's supposed to happen in ubuntu. 

During the update I noticed lots of "Perl: warning <text>" among other errors.

Do I need to do a complete install with a cd or is there some way to fix this?

---

### Post by tgalati4 on 2007-05-04
Try booting with a Dapper Live CD.  Mount your hard drive:

sudo mount /dev/hda1 /mnt/hda1

Examine /var/log and see if there are any unusual errors.  Probably Xorg crashed.  Check xorg.0.log and see what tripped it up.

It may be a simple fix.

---

### Post by thinman1189 on 2007-05-05
I have two hard drives and I'm not sure what it would read as the first one. How do I find out the order?


This sounds like a "boot to black" issue I read about in another post. I'm searching for help on that at the moment.


update: just deleted all instances of splash quiet and quiet splash from the command lines. it didn't help. now contral alt del doesn't work.

i just want to update to fiesty once i've got edgy, so if i could just skip fixing edgy that'd be great.

---

### Post by tgalati4 on 2007-05-05
It's probably better to do a backup of /home and wipe the disk and do a fresh install of Fiesty.  Boot the Live Feisty CD first to make sure you can run most things out of the box.  If many things are broken in the Live CD then you will have that many problems to solve after the install.

The drives are listed in a file

/boot/grub/device.map

dmesg | more

will also enumerate the drives and print out some descriptive information.  You have to page through the file to find the information.

Or if you feel lucky:

dmesg | grep hda
dmesg | grep hdb
dmesg | grep sda
dmesg | grep sdb

If your goal is Feisty, then fresh install is recommended.

---

### Post by thinman1189 on 2007-05-13
/dev/sda1 is not removable
could not execute pmount

I put in my dapper cd and tried to mount to get my data off of the drive. I need some of the work fast. What should I do?

---

### Post by tgalati4 on 2007-05-13
Panic.

What kind of disk drives?  IDE or SATA?  Feisty labels SATA drives as SCSI drives (/dev/sda1).  Dapper labels USB sticks as /dev/sda1.  This is probably where the confusion is occuring.

What does dmesg say that your drive is called in Dapper?  Probably /dev/hda1.

sudo mkdir helpmeIneedmydatarightnoworImagonnadie
sudo mount /dev/hda1 helpmeIneedmydatarightnoworImagonnadie

Let the data recovery begin.

---

### Post by thinman1189 on 2007-05-14
> **tgalati4 said:**
> Panic.

What kind of disk drives?  IDE or SATA?  Feisty labels SATA drives as SCSI drives (/dev/sda1).  Dapper labels USB sticks as /dev/sda1.  This is probably where the confusion is occuring.

What does dmesg say that your drive is called in Dapper?  Probably /dev/hda1.

sudo mkdir helpmeIneedmydatarightnoworImagonnadie
sudo mount /dev/hda1 helpmeIneedmydatarightnoworImagonnadie

Let the data recovery begin.

It's a SATA drive.

Is that code serious? :?

---

