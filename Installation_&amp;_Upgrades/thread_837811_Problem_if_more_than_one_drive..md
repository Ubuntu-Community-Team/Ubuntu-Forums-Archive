---
title: "Problem if more than one drive."
date: 2008-06-22
forum: Installation &amp; Upgrades
---

### Post by A Traveller on 2008-06-22
Hi All.

I have a W98SE hard drive as my main drive. I then added another hard drive to my computer and installed Ubuntu (LTS 6.06) on it.

Upon restarting at the end of the installtion process, the full installation loads with the Ubuntu desktop and everything works perfectly, BUT at the next startup, during the boot up process a whole load of errors are listed and it doesn't start.

Uncompressing Linux: Ok, booting the kernel.

Mount: Mounting dev/hda1 on root failed: No such device
Mount: Mounting root/dev on /dev/ .static/dev failed: No such file or directory
Mount: Mounting sys on/root/sys failed: No such file or directory
Mount: Mounting proc on/root/proc failed: No such file or directory

Target file system doesn't have /sbin/init

/bin/sh: cam't access tty: job control turned off.


Why does is work fine immediately upon installation and then not boot at any consequent times?? I have used an original Ubuntu CD.

Sometimes, it gets as far as the screen with the Ubuntu logo with a scrolling list of various checks on drivers, etc underneath.

I managed to figure out the only way to get Linux to load: Remove my other hard drive (W98SE)  and replace it with the Linux hard drive. Even completely disconnecting the W98SE hard drive and setting the Linux hard drive as the first boot device doesn't work! Only works if the W98SE hard drive is replaced with the Linux one!!

I want to be able to leave both hard drives in the computer and choose whichever one I want to boot into, not keep having to replace them all the time!!

Any advice on this problem would be more than appreciated!

Thanks.

---

### Post by Pumalite on 2008-06-22
Do you have a mix of SATA and IDE? Did you disconnect a drive during installation?

---

### Post by A Traveller on 2008-06-23
Hi Pumalite, thanks for your response.

No, I don't have a mix; it's just IDEs. No, I didn't disconnect any drives during installation.

I don't think the problem lies with the hard disks or that there may have been a glitch during installation because I have tried it on two different hard disks and more than once and the same thing happens everytime.

---

### Post by Pumalite on 2008-06-23
Try to boot Knoppix Live CD:
[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)

---

### Post by A Traveller on 2008-06-25
Thanks for the suggestion. Am currently taking a look this.

---

### Post by Pumalite on 2008-06-25
Good luck.

---

