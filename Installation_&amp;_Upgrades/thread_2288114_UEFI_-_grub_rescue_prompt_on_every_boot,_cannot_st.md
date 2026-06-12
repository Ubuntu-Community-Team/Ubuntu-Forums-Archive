---
title: "UEFI - grub rescue prompt on every boot, cannot start system"
date: 2015-07-24
forum: Installation &amp; Upgrades
---

### Post by mslinn on 2015-07-24
My pastebin is here: [http://paste.ubuntu.com/11923261/](http://paste.ubuntu.com/11923261/)
The grub rescue> prompt does not recognize the initrd or boot commands
My BIOS says UEFI when it boots.
Someone please help me!

Thanks,

Mike

ps: my profile is locked so I cannot update it with current system information.

---

### Post by oldfred on 2015-07-24
Can you boot from grub rescue?
 Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

      
 grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. Change if not hd0,1.
configfile (hd0,1)/boot/grub/grub.cfg
OR:

 set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
linux (hd0,1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,1)/initrd.img
boot

I just noticed that 14.10 reached end of life on July 23.

You seem to have booted Boot-Repair in UEFI mode. So you have UEFI capable hardware, but both installs are BIOS based. Better to boot Boot-Repair in BIOS mode then.

I started converting all drives to gpt partitioning several years ago (actually with my install of 10.10), and then started adding both an efi partition for future use and a bios_grub partition as system was BIOS only. Then drives would be compatible with new system. But just installed my first UEFI system last fall.

You may want to houseclean old kernels also. I try to keep two, but let it grow to 3 or 4 can then delete back to 2, typically. I prefer to use synaptic and search for linux-image.
      
 Check current kernel I also keep one older just in case:
#Current kernel:
uname -a
# kernels, shows older also?
dpkg --list | grep linux-image

I also prefer to have smaller system partitions and large data partitions. I use 25GB for / (root) including /home. But the only things in /home are the user settings and my .wine for Picasa, as I understand trying to move it is a bit more problematic. But all my data is in /mnt/data and other data partitions, backup partitions on each drive, and several other installs.

---

### Post by mslinn on 2015-07-24
Unknown command: configfile. Same also true for initrd and boot commands.
This system was upgraded to 15.04, not sure why the older version was reported.
Housecleaning sounds great, but I need to be able to boot first. Cannot run uname or dpkg, because I cannot boot.
The discussion about messing with partitions is a bit premature.
How do I "boot Boot-Repair in BIOS mode"? There is no menu when the system boot - the "grub rescue>" prompt shows up first.
Before I ran boot repair I used to see a boot menu. No more.

Thanks,

Mike

---

### Post by mslinn on 2015-07-24
I tried Super Grub 2, and found that several kernels gave "Error - invalid magic number", however 3.16.0-34 was the newest that did not give the error. Glad I kept it.
Fsck reported lots of errors, then tried to continue loading. System stopped and the became unresponsive.

I then tried booting from the 14.10 image on the backup drive (backed up last night). Again fsck showed lots of errors, but the XUbuntu blinking dots appeared. I selected F to automatically fix errors. The drive looked busy for a while, then the screen went black and drive activity stopped.

I guess I am well and truly screwed. Is there any hope to recover?

Mike

---

### Post by oldfred on 2015-07-24
Since your 14.10 install is now past support, you will not easily be able to fix by uninstalling and reinstalling or updating anything as repositories are closed. If fsck does not fix it and Supergrub will not boot it, then it may be difficult to fix. But if you copies it from sda to sdb, then all its setting in fstab and grub still refer to sda and trying to directly boot it.

So 15.04 in sda, is an upgrade and sdb1
I did not notice this before and it is a major issue as you cannot have duplicate UUID.
/dev/sda1        ca308c55-afef-4de3-8cf7-a218f60aa9d4   ext4       
/dev/sdb1        ca308c55-afef-4de3-8cf7-a218f60aa9d4   ext4       

Either unplug sdb1, or immediately change its UUID.

Change UUID see also man pages, example is sdaX, you want sdb1:
 uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX

---

