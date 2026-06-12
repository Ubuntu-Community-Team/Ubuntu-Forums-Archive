---
title: "Need to boot from /dev/sda2 - getting Error 21"
date: 2006-08-20
forum: Installation &amp; Upgrades
---

### Post by skecherkid on 2006-08-20
I have installed Mepis on a USB mini-harddrive out of necessity as my laptop runs Windows and its company owned and I *dare not* try to change anything of the Windows installed on the main hard drive.

I booted from the "liveCD" and MEPIS saw my mini Hard drive fine and I used QParted to resize the exsting mini-drive FAT32 partition to 512mb (its minimum) and then created a new ext3 partition with the rest of the space on the mini drive.  That made the new ext3 partition the /dev/sda2 and I installed MEPIS on that without (as far as I could *tell*) any issues.

When it asked about where to put MBR and some GRUB questions I told it to put it on /dev/sda2 'cause I did NOT want anything to happen to my Windoze MBA on /dev/hda1

So when I boot my laptop it boots Windows as normal, unless I change the boot sequence to start with my USB HDD.  When I tried booting from the USB HDD to test out my MEPIS install I got the GRUB error 21 Selected disk does not exist

The line it was on was 
root (hd2,1)

Which I would think is correct because the laptop has 1 harddrive internal, a pcmcia harddrive as a backup, and then my new USB HDD.  

When I booted again from the mepis CD I used a utility to list the drives:
/dev/cdrom
/dev/fd0
/dev/hda1 ntfs (main boot)
/dev/hda2 ntfs (2nd partition of Windows)
/dev/hda3 vfat (I think this is "hidden" partition IBM set up as a system restore)
/dev/hde1 ntfs  (pcmcia)
/dev/sda1  vfat
/dev/sda2  ext3   (where I installed mepis and grub)

Hmmm so I am a completely newbie at this - any idea on what my problem with this is?  Do I need to use initrd for booting this way maybe?  If so,  where is a good place to learn about that?  (me knows nothing!)

Help and thanks!

---

### Post by skecherkid on 2006-08-21
Hmmm...update on this.

When I figured out the command line in grub I was able to determine that the pblm was that the USB HDD ext3 partition is (hd0,1) when the USB HDD is used as boot.  

Now though - I get a kernel panic when it starts booting:

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

Eeeks! Now searching the forums on the new error...

---

