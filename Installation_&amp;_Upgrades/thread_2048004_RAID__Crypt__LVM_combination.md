---
title: "RAID / Crypt / LVM combination"
date: 2012-08-25
forum: Installation &amp; Upgrades
---

### Post by DiagonalArg on 2012-08-25
***After an error that turned out to be a known grub issue, I'm back to my two questions in this post.***
***How to avoid putting in two passwords for my disks?***

Hi all.  Starting an install & a bit unsure on a couple of points with a RAID/LUKS/LVM combination.  In condensed form I have a 2T and a 1T disk.  I am doing:

(1) 512MB primary @ beginning of both disks -> Use for RAID -> Setup RAID -> Mount as /boot

(2) 999.7 GB extended partition both disks -> Use for RAID -> Setup RAID -> Use for Crypt#1

(3) 1TB logical partition on (unRAIDed) remainder of 2T disk -> use for crypt#2

(4) Setup Crypt.  It asks for passwords for both encrypted partitions.  I use the same on both.

(5) Set both encrypted partitions to be used for LVM

(6) (not done yet) Configure the logical volume manager and create /, /home, swap on VG based on Crypt#1 and /backup on VG based on  Crypt#2

Questions:
(1) I am confused about putting in two passwords.  Does that mean when I boot up it'll have to ask for two passwords?  I would obviously prefer to put in one.

(2) I was trying to consider if there is another order in which to do this.  Should I use all of my free space for LVM first (one raided and one not), and then use that for Crypt??

Thanks in advance!

---

### Post by DiagonalArg on 2012-08-26
Well, I did #6 and started to install.  All was well until I got  to installing Grub.  Perhaps someone can tell me what I'm doing wrong?

> 
Unable to insatall grub in /dev/sda
Executing `grub-install /dev/sda' failed
This is a fatal error.When I check the terminal, I find:

> 
Installing grub on `/dev/sda'
grub-install supports --no-floppy
Running chroot /target grub-install --no-floppy --force "/dev/sda"
/usr/sbin/grub-probe: error: no such disk.
Auto detection of a filesystem of /dev/mapper/root--raid--crypt--lvm-root failed
Try with --recheck.
If the problem persists please report this together with the output of "/usr/sbin/grub-probe --device-map="/boot/grub/device.map" --target=fs -v /boot/grub" to <bug-grub@gnu.org>
error: Running 'grub-install --no-floppy --force "/dev/sda" failed.
File descriptor 3 (pipe: [6728]) leaked on lvdisplay invocation. Parent PID 27893: /bin/sh
File descriptor 4 (/dev/pts/0) leaked on lvdisplay invocation.  Parent PID 27893: /bin/sh
File descriptor 5 (/dev/pts/0) leaked on lvdisplay invocation.  Parent PID 27893: /bin/sh
File descriptor 6 (/dev/pts/0) leaked on lvdisplay invocation.  Parent PID 27893: /bin/sh
main-menu[410]: WARNING **: Configuring 'grub-installer' failed with error code 1
main-menu[410]: WARNING **: Menu item 'grub-installer' failed.
init: starting pid 380, tty '/dev/tty2': '-/bin/sh'
init: starting pid 381, tty '/dev/tty2': '-/bin/sh'
So I do as they say and run the command grub-probe ...  (these results may have run off the top, I can't tell):

> 
Found array md/0 (mdraid1x)
Scanning for mdraid1x RAID devices on disk hd1.
the size of hd1 is 1953525168.
the size of hd1 is 1953525168.
Scanning for mdraid1x RAID devices on disk hd1,msdos5.
the size of hd1 is 1953525168.
Scanning for mdraid1x RAID devices on disk hd1,msdos1.
the size of hd1 is 1953525168.
scanning md/0 for LVM.
no LVM signature found.
scanning md/1 for LVM.
no LVM signature found.
scanning hd0 for LVM.
the size of hd0 is 3907029168.
no LVM signature found.
the size of hd0 is 3907029168.
scanning hd0,msdos6 for LVM.
the size of hd0 is 3907029168.
no LVM signature found.
scanning hd0,msd5 for LVM.
the size of hd0 is 3907029168.
no LVM signature found.
scanning hd0,msdos1 for LVM.
the size of hd0 is 3907029168.
no LVM signature found.
scanning hd1 for LVM.
the size of hd0 is 1953525168.
no LVM signature found.
the size of hd0 is 1953525168.
scanning hd1,msdos5 for LVM.
 the size of hd0 is 1953525168.
 no LVM signature found.
scanning hd1 for LVM.
 the size of hd0,msdos1 is 1953525168.
 no LVM signature found.


---

### Post by DiagonalArg on 2012-08-26
I have now  checked integrity of the install disk, and it is fine.

The hardware I am using is a Tyan S2865 with 4G memory and an Opteron 170.  BIOS is latest, but it's for the barebones server.  I'm going to try to flash the same version (also latest) for the desktop machine.

---

### Post by DiagonalArg on 2012-08-26
Ok, so I flashed the BIOS and reinsalled Ubuntu.  This time, Grub  installed (apparently) correctly, and I was able to complete the install  of Ubuntu.  Unfortunately, the machine does not boot.  I am looking at  it again from the live CD.  I can assemble the RAID arrays, mount /boot,  and unlock the encrypted disks, revealing the Logical Volume Groups.  I  can mount the LV that is RAIDed and contains swap,/root,/home (but not  the one that is unRAIDed).

The only other thing I can add is that as I try to boot, the BIOS checks for a floppy, a CD, and then it says:

> 
error: No Video Mode Activated


before jumping to a black screen and sitting there forever.

Any help would be appreciated!

---

### Post by DiagonalArg on 2012-08-27
Ok, the "no video mode activated" error seems to be a known grub problem:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/699802](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/699802)

Suggestion #28 worked, I've installed the nVidea drivers, and will be experimenting with #24 next since the boot screen has screwed up fonts, even if I can see enough to decrypt my disks.

But ...

I'm back the the questions in my first post.  When I boot up, I have to put in passwords for both cryto disks.  How do I get around this so I can just use one password?  Is there another way/order in which to do RAID/Crypt/LVM that will avoid this issue?

---

