---
title: "Grub error 15"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by speedymon on 2008-01-30
Well i powered up my dell 1705 one day and got a grub error 15.  After digging through some threads i finally reinstalled grub with the help of the Live CD.

Now when i boot up i go straight into the grub setup (grub>).  I noticed i don't have a menu.lst file however.  Also noticed that when i do a "root hd0 or root hd0,0 i don't get any information back about my partition.

I installed grub on (hd0) and (hd0,0) with no success.  What am i doing wrong?

---

### Post by logos34 on 2008-01-30
from the live cd you did

sudo grub

> root (hd0,0)
> setup (hd0)
> quit

?

---

### Post by speedymon on 2008-01-30
quit isn't a supported command .....odd.  I'll try that combo but i think i did that and it didn't work

---

### Post by logos34 on 2008-01-30
> **speedymon said:**
> I noticed i don't have a menu.lst file however.

oops, missed that.

Are you sure? Boot from the live cd, mount root and check /boot/grub

---

### Post by speedymon on 2008-01-30
I'm positive.

---

### Post by speedymon on 2008-01-30
Last line after running grub> setup (hd0) is:

Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2 /boot/grub/menu.lst"...succeeded
Done.

grub> quit

Erro 27: Unrecognized command

WTF????

This is not using the live cd;  it boots right to the grub prompt.

---

### Post by logos34 on 2008-01-30
try a [direct boot]("http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot.").

If it gets you into ubuntu run **sudo update-grub **to generate new menu.lst

---

### Post by speedymon on 2008-01-30
at the kernel /vmlinuz root=(hd0,0) command i'm getting Error 15:  File not found.

grub>  find /sbin/init returns (hd0,0)

no menu.lst file

device.map says:

(fd0)     /dev/fd0
(hd0)    /dev/sda

??????

---

### Post by speedymon on 2008-01-30
Digging around some more...

/boot/vmlinuz-2.6.22-14-generic does not exist.
/boot/initrd.img-2.6.22-14-generic does not exist.

these are files that need to be here right?

---

### Post by logos34 on 2008-01-30
no telling what happened.

Maybe start thinking about backing up saved files to USB drive and reinstalling.

You could try booting using the Super Grub Disk, but if you can't find the vmlinuz and initrd.img it may be a waste of time.

---

### Post by speedymon on 2008-01-31
The vmlinuz and initrd.img symbolic links are there in the / directory, but no files in the /boot directory.  Can i just replace them?

---

