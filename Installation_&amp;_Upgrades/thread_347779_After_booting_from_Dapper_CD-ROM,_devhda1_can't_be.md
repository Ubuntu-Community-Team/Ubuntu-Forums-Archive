---
title: "After booting from Dapper CD-ROM, /dev/hda1 can't be mounted (so can't fix grub...)"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by Phrawm48 on 2007-01-27
After booting from the Ubuntu 6.06 LTS CD-ROM, I'm unable to access or even mount my computer's hard drive, a.k.a. /dev/hda1, a.k.a. "C:".

-- If I use fdisk -l, I can see /dev/hda1 listed.  The information for hda1, including the "boot asterisk" indication and the size and type of drive, is also correct.

-- If I use the GUI "Disks" tool, it sees /dev/hda1 but won't allow me to Enable it, and thus to browse -- or more important -- write to, it.  Other USB drives are, however, automatically mounted when the drives are  powered on.

-- The "C:" drive boots directly and smoothly into windows (no hardware problems), and after booting I can use Partition Magic to browse my Linux partitions and all.

Regarding the last item, I used Norton Ghost 2003 to copy a STILL-working multi-partition drive to the current misbehaving drive.  Doing this broke grub, so I used the W2K Pro CD-ROM to run fixmbr.  Okay, the system now boots smoothly into W2K, but my next problem became repairing Grub per this How-To:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

But I can't fix grub because the Ubuntu CD-ROM won't let me enable /dev/hda1 so that I can make the MBR dual-bootable again...

Any ideas, anyone?

Cheers & thanks,
Riley

(P.S.  I wanted to Ghost my Linux partitions before trying to update the driver for my graphics card.  The idea was that if I broke something when doing that I could easily get back to a working system.  Ha, ha. ain't Linux fun? -- my problems are now nested three-deep!)

---

### Post by bernied on 2007-01-27
/dev/hda1 is the first partition on the hard drive, not the whole drive.

Can you please post the output of:
sudo fdisk -l

And clarify what you want to do:
- is it to reinstate dual-booting after altering the MBR doing something windowsish?
- fix a faulty grub configuration (menu.lst)?

What happens when you boot? Do you get a grub menu or does it boot straight into windows?

And while you're waiting for your next reply, I suggest you get yourself a [super grub disk](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html) (if you can burn a cd)

---

### Post by bernied on 2007-01-27
Is it this line in the howto that you are having trouble with:
```
mount -t ext3 /dev/hda1 /mnt/root/boot
```
This will attempt to mount the first partition on the first drive, with an ext3 filesystem, onto the location /mnt/root/boot
But, if as you say, /dev/hda1 is your windows C: drive, then it will not have an ext3 filesystem, it is probably ntfs.
But, you don't need to mount that partition anyway, because that's not where your grub files are, or is it? Normally your grub files would be on the linux partition, which probably is ext3.

Following a howto word-for-word will only work if you have the same setup as the person who wrote the howto.

If you are just trying to reinstate the grub MBR, you can adapt that first method in the howto - you don't need to mount anything, like this (but don't use (hd0,3) unless that is where your grub files are located, use the output from the find command):
> ###Not an exact quote...
1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal. Open a root terminal (that is, type "su" in a non-Ubuntu distro, or "sudo -i" in Ubuntu). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,3)".

**6. Type "setup (hd0)".**

7. Type "quit".

8. Restart the system. Remove the bootable CD. 

---

### Post by Phrawm48 on 2007-01-27
Okay, some more information.

MY GOAL is to repair grub on an 80 GB IDE hard drive that received a Ghost image of a working W2K Pro / Ubuntu dual-boot configuration.  The multi-partition source drive for the Ghost image works properly: On it, I receive a grub prompt, and can use it to boot smoothly into either Ubuntu or W2K Pro.

After copying the Ghost image to a second 80 GB from a different manufacturer, I received only a "grub " prompt, at which point the system went no further.  I remedied this by using the W2K CD-ROM to run fixmbr, thus allowing me to boot into Windows but completely removing all grub information.

I then booted off the Ubuntu CD-ROM and am trying now to get grub dual-booting back on the new drive.  (Note -- I tried along the way to burn a bootable super grub CD but I  couldn't boot from it.  I hope I can avoid digressing into solving that problem for the moment...)

Here's a look at the system.

------ Begin command examples ------

sudo -i
root@ubuntu:/boot# uname -r
2.6.15-23-386

root@ubuntu:~#fdisk -l
Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4204    33768598+   7  HPFS/NTFS
/dev/hda2            4205        4212       64260   1e  Hidden W95 FAT16 (LBA)
/dev/hda3            4213       10011    46580467+   f  W95 Ext'd (LBA)
/dev/hda5            4213        4479     2144646   82  Linux swap / Solaris
/dev/hda6            4480        4494      120456   83  Linux
/dev/hda7            4495        8692    33720403+  83  Linux
/dev/hda8            8693       10011    10594836    b  W95 FAT32

Note that this command also listed some USB drives which I didn't include because it didn't seem pertinent...

Then (as su):
grub
grub> find /boot/grub/stage1
Error 15: File not found

------ end command examples ------

Yes, "/dev/hda1" is an NTFS partition (not a drive as I stated in my initial post).

Note too that along the way I booted up W2K Pro and used Ghost 2003 to view the image of the above multi-partition drive.  The Ghost image file contained a WHOLE bunch of files, both under the Linux /boot partition and under the grub sub-directory, that were not present on the current drive.  So I used Ghost and Partition magic to copy the files from the image back into the drive.  Here's the contents of the current /boot/grub directory:

root@ubuntu:/boot/grub# ls -l
total 188
-rwxrwxrwx 1 root root    197 Jan 28  2007 default
-rwxrwxrwx 1 root root     30 Jan 28  2007 device.map
-rwxrwxrwx 1 root root   7508 Jan 28  2007 e2fs_stage1_5
-rwxrwxrwx 1 root root   7332 Jan 28  2007 fat_stage1_5
-rwxrwxrwx 1 root root   8128 Jan 28  2007 jfs_stage1_5
-rwxrwxrwx 1 root root   4319 Jan 28  2007 menu.lst
-rwxrwxrwx 1 root root   3993 Jan 28  2007 menu.lst~
-rwxrwxrwx 1 root root   6804 Jan 28  2007 minix_stage1_5
-rwxrwxrwx 1 root root   9076 Jan 28  2007 reiserfs_stage1_5
-rwxrwxrwx 1 root root    512 Jan 28  2007 stage1
-rwxrwxrwx 1 root root 105428 Jan 28  2007 stage2
-rwxrwxrwx 1 root root   8764 Jan 28  2007 xfs_stage1_5
root@ubuntu:/boot/grub#

Finally, in Gnome is it important that I CANNOT use System > Administration > Disks to *Enable* the NTFS partition for browsing, and thus writing?  In fact, I had to use the GUI Disks tool to enable my disk-based root and /boot partitions so I could browse them for purposes of collecting the above information.

I'm baffled...

Cheers & thanks all,
Ric
SFO

---

### Post by Phrawm48 on 2007-01-28
Okay, I'm up on my second, Ghost'ed drive.

I created a Super Grub CD (0.9550) and was able to make the target drive once again dual-bootable.  For those chasing the same problem, this page was highly informative:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Here's the link to the Super Grub CD:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

The CD version is MUCH easier to use than the floppy version (I tried both).  This hideously formatted page explains how to create either:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Long story short, you'll want to get an .iso image of the most recent version of Super Grub onto a CD, boot from it, then follow the prompts.

I'm now happily up on my second, Ghost'ed drive but still would like to understand why I had so much trouble doing it from the CLI.  I'll figure that out some other day...

Cheers and thanks to all who responded,
Ric
SFO

---

