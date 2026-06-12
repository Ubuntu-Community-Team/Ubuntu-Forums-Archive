---
title: "How do you enable usb-creator-gtk options for persistence"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by dakra137 on 2010-05-02
Whether started as usb-creator-gtk from a terminal, or from the Gnome menu System/Administration/StartupDiskCreator, the option for persistence is grayed out with the Discarded option preselected.

UBUNTU 10.04 
usb-creator-gtk 0.2.22
The USB is formatted with FAT32.

MakeStartupDisk creates a bootable USB stick without persistence.
There is a casper directory, but no casper-rw file.

---

### Post by dakra137 on 2010-05-02
WORKAROUND:

1) Build the nonpersistent bootable live usb with usb-creator-gtk

2) Create, format, and copy a casper-rw file as described at [http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/](http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/)

[INDENT]
dd if=/dev/zero of=casper-rw bs=1M count=4000
mkfs.ext3 -F casper-rw
[/INDENT]
copy it to the root of the USB drive

3) Add a paragraph to /syslinux/text.cfg on the USB drive

[INDENT]label persistent
menu label ^Run UBUNTU from USB with persistence
kernel /casper/vmlinuz
append noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz --
[/INDENT]

4) change the first line of /syslinux/text.cfg to
[INDENT]default persistent[/INDENT]

---

### Post by Herman on 2010-05-03
After you erased the disk ready to install the Live CD in it, did you try clicking on the partition you want to use for installing the Live CD files in?

Because every time I do that the options at the bottom of the 'Make Startup Disk' Windows that were greyed out come to life, then I can easliy adjust the slider to allow the amount of reserved space I want to persistence, it seems easy enough to me.

---

### Post by dakra137 on 2010-05-03
That didn't help, no matter whether clicking on the device, the partition, or whether it had been mounted or not: Still grayed out.

---

### Post by guv999 on 2010-05-09
Hi - I am having same issue - all the persistence options are greyed out when attemted to make a bootable drive.  Any help as how to enable them appreciated

---

### Post by dakra137 on 2010-05-09
After using the USBuntu Live a bit, I realized it's not what I wanted.  The Live drives are meant primarily for doing installations, not "run on your system on whatever machine is around." 

Instead, I did an INSTALL from CD onto an 8GB stick. I set it up as 6GB EXT3 root and 2GB SWAP. Click on ADVANCED options to install the boot manager onto the stick too.

For maximum portability, do not activate any special drivers for the video card on the machine you install at.

---

### Post by shinjan on 2010-05-09
I am using ubuntu 9.10...now I have created an USB startup disk in my 1gb pen drive with a persistence region of 200MB. But after I have booted into the live ubuntu version using the pen drive how will I access the reserved space?.. I have tried mounting the pen drive but still couldn't access the reserved space...
pls help
NB:-I have only one FAT32 partition in my pen drive...

---

### Post by astyonax on 2010-05-21
Hi! 
I've found that if usb-creator-gtk auto-find the .iso on the Desktop, then persistence options are disabled,
instead, when I moved the file on my home, and the program couldn't find it, I selected manually the file and persistence options correctly become available.

Hoping it was useful,
Bye.

---

### Post by jimothy on 2010-05-31
@astyonax. i have found the same thing. If you select a different iso than the one that is automatically found, the persistance options become available.

---

### Post by C.S.Cameron on 2010-06-01
Following is a method of adding a persistent partition:

Boot Live CD.
Plug in flash drive.
Start Partition Editor
Create 1 GB FAT32 partition, (on the left side of the bar). (size is optional)
Create a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw". (ext2 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, run "gksu nautilus"
Select disk / syslinux / text.cfg and added "persistent" as shown below:
append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
Shutdown, remove CD, reboot.
You are persistent.

---

### Post by vs8 on 2010-06-07
Yes, when moving the file and manually choosing it, the options come to live. What a stupid bug. Can someone fix this usability bug?!

---

### Post by rg_stephens on 2010-06-13
I had two partitions on my external drive: One is my backup drive, the other was to be a Boot Disk. So I selected the partition I wanted, and everything was greyed out. I assumed something was wrong, so I clicked "erase", and BOTH PARTITIONS were deleted!!!!!!!!

I guess I'll never see that data again:mad:

---

### Post by bmullan on 2010-07-12
> **dakra137 said:**
> That didn't help, no matter whether clicking on the device, the partition, or whether it had been mounted or not: Still grayed out.

I found that using this tool I was at first seeing this same problem where the Slider "**Store in Reserved Extra Space**" was **greyed out**

I had tried selecting my .iso image from my Download directory, I tried moving it to my Home directory as someone suggested but neither worked.

What I finally figured out was that AFTER you select the .iso image from your disk I had to CLICK on the form entry line containing the path to that .iso file I had selected.      

You click in that window on **/home/yourname/whatever.iso**

Assuming you are using a fresh formatted USB thumb drive when you click/select that image path/name _**then**_ the "greyed" area activates.

I guess its more of bad human interface design for this particular tool as there is no obvious clue to what un-grey's that bottom section out.

---

### Post by Slim Backwater on 2010-07-21
The bug is 557775.

[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/557775](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/557775)

---

### Post by HeadHunter00 on 2010-09-27
it seems running the program as root solves the problem, which means that either the configs are messed up, or it doesn't have proper permissions. if only i knew where usb-creator-gtk stored its configs.

---

### Post by kutalion on 2010-10-11
This one's clear (almost). I am in need of something a bit different. A month ago my hard drive fried up and since then I've been using Puppy Linux as a savior since it has automatic persistence. Recently I've found that Ubuntu has too (what a happy happy moment) but there comes another problem. I can't use persistence since my lappy can't boot from flash drives so I had to do it the old fashion way CD + Flash (the way I do it in this very moment with Puppy) and... I failed. I'd write persistent at the boot options but to no avail. Every time it starts a new and every time it doesn't even notice that I have a flash drive with casper-rw or casper-cow on its / mounted in the system.
Is there any hope or is it just a lost cause?

---

### Post by C.S.Cameron on 2010-10-11
Casper-cow is really old and no longer works.
Casper-rw works with some recent versions of Ubuntu.
Type a space before "persistent".

---

### Post by kutalion on 2010-10-11
I tried adding space after "--" I tried without adding space after this and I tried adding "persistent" before "--" to no avail. Right now I'm trying the workaround in the second post although it's for USB. I suppose the boot commands line should be quiet the same. We'll see.

EDIT: It was a mission impossible. After I burn the disk it would check integrity forever because of the edited txt.cfg .

EDIT2.0: Ok, it seems that the CD won't bite casper-rw file from any drive.That's no big deal because I finally made it possible to boot from a USB. I created 550MB of bootable vfat system (for Lubuntu since Ubuntu is to heavy to be run from flash and slows down like hell) where I moved the files from the .iso with unetbootin and then the existing unpartitioned space on the thumb drive I formated with ext2 partition named casper-rw. It seemed to run pretty faster.

---

