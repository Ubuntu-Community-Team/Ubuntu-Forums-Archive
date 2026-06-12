---
title: "Triple boot Vista, FreeBSD, and ubuntu"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by mgdubu on 2007-02-10
Triple Boot: Vista, FreeBSD 6.2, Ubuntu 6.1

Why Vista, am part of M$ collective that will be rolling out Vista at employer?
Why FreeBSD, worked with FreeBSD at previous employer maintaining web/mail services?
Why Ubuntu, have server with Symbol/Motorola product called MSP that has ubunutu as o/s?

My insanity...you can skip to "The Solution" if you wish...
1st attempt
Installed Vista first
Installed FreeBSD, rebooted and FreeBSD boot manager detects Vista
Installed Ubuntu, grub can't load FreeBSD

2nd attempt
Installed GAG (love GAG, will use again)
Installed O/S as in 1st attempt
GAG loads everything except ubuntu, I assume because it can't deal with ubuntu root and swap being on different partitions

3rd attempt
Installed Vista
Installed ubuntu
Installed FreeBSD selecting FreeBSD boot manager

The FreeBSD boot manager kills Vista's MBR.
Rebooted system with Vista CD and chose repair instead of install. This fixed the MBR so that Vista would load. 

Re-installed ubuntu on original partitions. Now, grub sees Vista and ubuntu and not freebsd. So, I had to launch grub and add lines for it to recognize presence of FreeBSD.

The Solution (For a 75 GB drive).


1) Using M$ Enterprise Solutions CD, boot system and install Vista on a 25 GB partition, leaving 50 GB unallocated.

2) Install FreeBSD on a 25GB slice. Do not choose FreeBSD boot manager. I think, I chose use none. 

2) Put in ubuntu CD and boot system. Using gparted, create two partitions, one as ext3 and one as linux-swap. When you are on the format section, gparted may show 3 partitions including the one that Vista is on. Just select none for both the filesystem and partition to exclude this partition. Then choose / for the sda2 partition and linux-swap for the sda3. Here is how my drive types came up after I finished:

Partition    Filesystem     Mountpoint              Size          Flag

/dev/sda1    ntfs			4GiB	 boot

/dev/sda2    exts           /,/dev/.static/dev    25 GiB

/dev/sda3		 linux-swap                 510 MiB

/dev/sda4    unknown		                  25 MiB

3) How to tell ubuntu grub about FreeBSD...the unknown Filesystem.

When booted in ubuntu, go to Applications/Accesories/Terminal. At the prompt, type:

gksudo gedit /boot/grub/menu.lst

You will be prompted for your password. Scroll to the bottom of the menu.lst file and add the following lines:

title              FreeBSD
root 							 (hd0,3)
chainloader	       +1
boot

Note, the root line. FreeBSD is on sda4 partition. The syntax for the root command however counts from 0, so 3 represents the 4th partition. Save this and reboot, when the grub menu appears scroll down to FreeBSD.

Bye-the-Bay, here is grub's, default Vista lines:

title						 Windows Vista/Longhorn (loader)
root             (hd0,0)
savedefault
makeactive
chainloader       +1

Note, the root line, Visat is on sda1, the first partition, which is hd0,0. (hd0,0), means, first hard drive, first partition.

I think that is it. But, honestly, I can't remember well the order FreeBSD and then ubuntu or vice-versa. All I know for certain is that I have a working triple-boot system. I used good 'ol google to find references and hints. Too many to divulge and none of which gave a workable solution to my combination of o/s, but all of which got me closer to the target...including posts on the ubuntu forum...just giving back to the community.

---

### Post by iamajd on 2007-05-02
Well, this thread is 3 months old, but I thought I'd post this for anyone else who finds it.  The recommended way to boot FreeBSD from GrUB is with the following lines:```
title		FreeBSD 6.2
root		(hd0,0,a)
kernel		/boot/loader
boot
```The only confusing part of that might be the 'root' line.  Most likely, if you're editing menu.lst, you are familiar with GrUB's numbering system.  For me, my FreeBSD slices are in sda1, which is (hd0,0).  The 'a' at the end refers to the slice with FreeBSD's boot information.

---

