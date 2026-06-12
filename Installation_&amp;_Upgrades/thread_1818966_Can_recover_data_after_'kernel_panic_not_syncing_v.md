---
title: "Can recover data after 'kernel panic not syncing vfs unable to mount root fs' ?"
date: 2011-08-05
forum: Installation &amp; Upgrades
---

### Post by userx5 on 2011-08-05
I need to recover some data of the 'home' directory after kernel panic. Can I achieve that?

I was upgrading ubuntu 11.04, [[COLOR=blue][COLOR=blue !important][FONT=Verdana][COLOR=blue !important][FONT=Verdana]installed[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.linuxquestions.org/questions/showthread.php?p=4434687#") on usb.
Failed to upgrade because the main partition had no more space.
I moved one directory of about 100Mb to other partition, but it seemed  that in the main partition didn't appear those 100Mb free.
I restarted the computer expecting those 100Mb free.
And kernel panic.

[ 0.789567] Kernel panic - not syncing: VFS: Unable to mount root fs on unknow-block(8,1)
[ 0.789646] Pid: 1, comm: swapper Not tainted 2.6.35-22-generic #33-Ubuntu
[ 0.789716] [<c05c6468>] ? printk+0x2d/0x35


Thank you very much.

---

### Post by userx5 on 2011-08-06
I've booted with another ubuntu installed in another usb, and if I mount  the first usb which has the ubuntu with the kernel panic problem, on it  I just can see directories like 'boot', 'casper', 'dists', 'pool',  'syslinux', and files like 'casper-rw' or 'ldlinux.sys'.

The ubuntu is installed on usb, and my data in the 'home' directory is  inside the ubuntu, but because of the kernel panic I can not start the  ubuntu. How can I get my data in 'home' directory?

---

### Post by userx5 on 2011-08-06
The data can be recovered mounting file 'casper-rw':

> sudo mount casper-rw /media/directory -o loop

Now how can I repair that kernel panic?

---

