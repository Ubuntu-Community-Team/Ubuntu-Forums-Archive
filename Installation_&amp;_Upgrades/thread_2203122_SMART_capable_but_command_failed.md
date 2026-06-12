---
title: "SMART capable but command failed"
date: 2014-02-01
forum: Installation &amp; Upgrades
---

### Post by samaricsm on 2014-02-01
Every time I upgrade, it seems to get more and more difficult to do so.  So, when the upgrade from 13.04 to 13.10 failed, I said no problem, I will just burn a DVD and do a clean install.  Heck, I have been meaning to go to 64 bit any way.  Now is a good time.  Just to make it go smoother, I formatted the disk with Disks to all zeros, then rebuilt the partitions.

Reboot is a Red Screen Of Death (a dark red screen is displayed, no error messages, no text, no mouse pointer or prompts).  ctrl-alt-Fx anything will not yield a text screen to log into.  The three finger salute will not reboot.  Power cycle.  I hate having to power cycle.  It really grates on my nerves.  Boot into recovery mode.  Cannot do ANYTHING.  THE FILESYSTEM IS READ ONLY!  How can I fix anything if I can't make any changes?

Reboot.  Cannot even get to GRUB.  The system halts with the message, "Ultramode DMA Mode-6, SMART capable but command failed."  There aren't enough reboots in the world to change that message.  Power cycle again.  Have I mentioned how much I hate to power cycle?  After cycling back to choice of RSOD or recovery mode.

One more power cycle and I re-install from scratch again, just in case I missed some error message.  Once Install is complete, same two choices RSOD or recovery mode.

I use the install disk to bring up Lynux, the terminal screen for command access, but the filesystem is still RO.  Why?  I mean the Install disk wrote on the drive and it will do it again if I tell it to.  Why am I not allowed to?

ASUS mother board
AMI BIOS M3A78-EM HDMI ACPI rev 1602
AMD Phenom 9950 Quad core 2.6 GHz
Dram clocking 800Hz
AMD North Bridge Rev B3
4096 MB RAM

Any help or suggestions will be appreciated.

---

### Post by oldfred on 2014-02-07
If there are issues it converts to read only. 
When you boot to recovery mode that is always ro, but you can reset to read/write.

I might try a full fsck from live installer.
       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by RJARRRPCGP on 2014-02-12
Looks like the HDD may have a bad board. Good luck swapping the board on a hard disk drive when not experienced... :(

---

### Post by bc.haynes on 2014-02-12
Did you check md5sums when you burned the CD/DVD?

---

