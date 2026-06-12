---
title: "GRUB and Windows just won't get along"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by fourthirteen on 2007-05-14
Hey Gang, I'm a fresh linux user who just installed ubuntu on my computer.  Everything is working great, and I'm quite happy with it.  Windows is the problem. 

I partitioned the hard drive with the ubuntu live CD, GRUB didn't include the windows title, so I edited /boot/grub/menu.lst to add this:

title		WINDOWS XP
rootnoverify		(hd0,1)
savedefault
makeactive
chainloader	+1

When grub boots windows, it starts to boot and shows the windows boot screen.  after about a second the computer reboots itself and as though it was just turned on and goes back to the GRUB menu.  Any Ideas?

---

### Post by logos34 on 2007-05-14
Post your /etc/fstab file.  Maybe there's an error in the entry for your windows partition (hda2), or it's missing, which is why it can't mount and just restarts.

Or you could just try 'root' in place of 'rootnoverify' and see if that works.

---

### Post by fourthirteen on 2007-05-15
here is the /etc/fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda2       /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

'root' and 'rootnoverify' seem to have the same results, I tried that before with no luck.  Thanks for the help, David

---

### Post by logos34 on 2007-05-15
i misread your post...fstab is not the problem here unless you can't mount xp partition in ubuntu.  Does it show up in /media and can you access it?

As far as xp not booting from grub menu, there might be a problem with the ntfs partition resulting from resizing before ubuntu install.  Have you thought about booting from the xp install cd and running chkdsk with the repair option?

---

