---
title: "Installation fails at 'Install the base system.' Debootstrap error"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by kentmcn on 2010-06-06
I'm installing Desktop 10.04 with the Alternate CD, due to a RAID1 requirement. Things go fine until the base system is being installed--just after the partitioning. Then I get a lot of Debootstrap warnings that file://cdrom/pool/main/... was corrupt, then "Warning: Couldn't download package ..." There must have been a hundred or more packages that wouldn't load.

This is my third try, with two different verified-for-integrity multiple-times CDs. The second and third try I checked both CDs for integrity prior to the installation attempt. (I switched to another CD after the second failure). Results were the same for all three attempts.

The partitioning has a RAID1 and several ext4 and ext2 partitions as well as a swap partition on each of the two drives. 

Is ext4 solid?

I've had previous troubles with trying to install this machine, but this is earlier in the process. (Previous trouble was the system's not finding /boot/grub and dumping me to a grub-rescue> prompt. I didn't follow up on the rescue because I couldn't find the /boot partition. Turned out the grub directory was in /. /boot was missing--maybe because I put it at the end of the drive during the install?).

---

### Post by kentmcn on 2010-06-07
Solved. 

Though not how I would have liked. I re-installed the system, using the whole (RAID) drive, scotching all partitions except / (on RAID) and going back to the ext3 filesystem. The problem seemed to revolve around the /boot partition in the initial installs.  Though /boot was defined (separate from RAID), when I used 'ls' inside grub-rescue, no /boot existed. (The grub directory was found directly under root). 

I didn't make a separate swap partition, either. Hope it doesn't come back to bite me in performance.

---

### Post by timkoop on 2010-07-04
Hi everyone.  I'm adding my own experience to this thread.  I had the same problem that kentmcn described, except I was trying to install 10.04 server on one simple hard drive.  My CD was verified for errors multiple times on more than one machine.  When I manually picked ext3 instead of the default ext4, poof!  No more problems.
--
Tim

---

### Post by Crixi on 2010-08-02
Hi. i just have to put my experienses regarding the "debootstrap error".

1. I got no CD/DVD reader.
2. I booted from a USB drive (containing "ubuntu server 10.4" after the nice aplication [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/))
3. the installer did not find a cdrom.
4. skipped the cd/dvd drive recognition part, couse i dont have a drive to try to recognize.
5. After some time i got the error....:(
6. searched the web for the exact error text. found some old post at google
7. nothing helped me.
8. Tryed to somehow get the usb memory to work as a cdrom...
9. while error message still was showing i pressed "alt+f2" to get a prompt (first time i ever got to a promt from any linux installer :) ).
10. typed several kinds of commands that was not recognized. that was abit whats expected when randomly testing commands :)
11. typed "mount /dev/sdd1 /cdrom" and the usb drive was mounted to cdrom.
12. Then i reselected the task that was failing and the installer started to get forward agen.
13. now im just waiting for the rest to finnish. Hoping for no more errors.

I have to say its abit funny that one tiny command can make it work :)

---

