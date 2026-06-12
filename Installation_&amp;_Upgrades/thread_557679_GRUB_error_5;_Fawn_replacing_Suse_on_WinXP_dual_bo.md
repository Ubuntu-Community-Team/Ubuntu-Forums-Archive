---
title: "GRUB error 5; Fawn replacing Suse on WinXP dual boot"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by spaceboy909 on 2007-09-22
I've spent 2 solid days on this now, searching, scouring, ect.  I can't quite find the exact description of Linux partition and file system info that I need to determine what went wrong.

I had WinXP and Suse 10.2 as a successful dual boot setup.  Windows on drive 1, and Suse on drive 2.  For various reasons, I decided to replace Suse with Ubuntu.

I started with the standard LiveCD.  Live boot worked fine the first time (but I think I may have just been away from the computer during install).  The 2nd live boot gave various buffer IO errors, and then would eventually boot up.  I investigated this error for a bit and decided to try the AltCD.

Same problem.  Decided to go ahead with a full install.

Seemed to install fine, but upon reboot I got the GRUB error 5 and system halt.  After searching a bit, I found the recommendations for SGD.

To jump forward a bit, I tried every appropriate option in SGD, including advanced options, and the only repair I was able to make was to restore the Windows MBR.

There were 3 main errors that I got depending on which option I chose:

1) Error 15:  /grub/stage1 and /boot/stage1 -- file does not exist  (But they do, because I've checked them with Explore2fs from Windows

2) Error 17: file system not recoginized (IIRC, I got this when trying to boot the hda MBR at some point.......probably before I restored it)

3) Another error was that it couldn't find the 'conf' and 'menu.lst' files.  SGD offered 4 default locations to check, and none of the worked, but yet Explore2fs clearly shows that they are there.

Now, on to the possibilities of what I have probably done wrong, and where I'm a bit confused.

When I installed Fawn, I started with the guided installer, but then switched to manual because I wanted better control of it......and I probably screwed it up, although it seemed straight forward enough.

Ftr, the linux partition sizes:  Swap= @800Mb, Ext3=@145Gb, Root/Boot=@2.5Gb

I distinctly recall that the Ubuntu partitioner displayed the root (boot?) partition as #7 in the list.  Is that a possible problem right there?  Are there any restrictions on the partition count?

Explore2fs from Windows lists two partitions: hdb3, which contains a 'lost and found' directory, nothing more, AND hdb6, which is obviously the main Linux partition.

2nd question:  Why isn't Explore2fs showing the 3rd partition?  And what does the empty hdb3 represent?  

Now, I installed the demo of 7tools partition manager.  Here's what it shows for drive #2:

Part #     Type

 1           Primary NTFS             ....
 2           Primary Linux Swap2  761Mb
 3           Primary Linux Ext3      137Gb
 4           Extended                   ....
 5           Logical Linux Ext3       2.2Gb
 6           Logical NTFS              ....
 7           Logical NTFS              .....

So, it appears that my boot partition is logical instead of primary, which is the norm, correct?  But GRUB can still boot from logicals, right?

And there's the fact that the listing above shows the boot partition as #5, but when I installed Ubuntu, the partition manager showed it as #7.  Perhaps the manager's listing was inaccurate?

...... I just booted with SGD again, and tinkered with some grub commands that I found online.....with disappointing results.

The 'find' /vmlinuz ; /boot/linuz ; and /sbin/init, finds exactly zilch.  And I think it was the 'root' command that was giving me 'unable to mount partition' errors.

At what point are the partitions mounted?  After a successful GRUB load?

------------------------------  HERE'S MY MENU.LST FILE

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=24154d0f-2e5c-478b-a0f2-5e20a718c08d ro quiet splash grub
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=24154d0f-2e5c-478b-a0f2-5e20a718c08d ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


I'm exhausted.  I hope there's a solution for this.........besides reinstalling both OS's again.

---

### Post by meierfra on 2007-09-23
Your root partition  is not equal to /boot.  It contains all the files  except  /home and needs to be larger than 2.5 GB. I think 4GB is about the minimum and I recommend  around 10 GB.

---

### Post by spaceboy909 on 2007-09-23
I'm 4 pages back after only 12 hours?  Wow!  This place moves fast!

Bump.  Hope somebody can help.

---

### Post by spaceboy909 on 2007-09-23
> **meierfra said:**
> Your root partition  is not equal to /boot.  It contains all the files  except  /home and needs to be larger than 2.5 GB. I think 4GB is about the minimum and I recommend  around 10 GB.

Yeah, I knew I probably had the names of the partitions mixed up, but as far as the sizes go, they were recommended by Ubuntu itself, so I think everything is standard setup.

---

