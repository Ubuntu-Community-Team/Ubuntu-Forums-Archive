---
title: "install on external hard drive"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by Uolirod on 2008-01-05
Ok, I did look at all the threads I could find on this and on error 18. I have installed Kubuntu on an external drive and my BIOS does recognize the drive and will attempt to boot from it. When it does it gives the message:

> GRUB Loading stage1.5.


GRUB loading, please wait
Error 18

I would be very appreciative if someone could point me in a direction.  :)
Oh, and this is on a box with WindowsXP in a RAID1 setup which is why I didn't install GRUB on the internal drives.

---

### Post by Pumalite on 2008-01-05
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

---

### Post by Uolirod on 2008-01-05
Thanks for that direction, I was a little curious when I installed as to why it didn't create a boot partition because the last time I'd installed Ubuntu the installer had. I'll just reinstall the whole thing and create a boot partition this time. Thanks again.

---

### Post by Pumalite on 2008-01-05
You are welcome. Good luck.

---

### Post by Uolirod on 2008-01-05
Well, at least I'm getting a different error now, Error 2.

> The general way that the Stage 1.5 handles errors is to print an error number in the form Error num and then halt. Pressing <CTRL>-<ALT>-<DEL> will reboot.

The error numbers correspond to the errors reported by Stage 2. See Stage2 errors. 

2 : Bad file or directory type
    This error is returned if a file requested is not a regular file, but something like a symbolic link, directory, or FIFO. 


Now I don't know exactly where to look for this 'file or directory' but I'm not really skilled at reading code.  :-k

---

### Post by Pumalite on 2008-01-05
Installing to an external hard drive is difficult. A lot of times Grub gets half installed in sda and half in the external drive. I have solved that problem disconnecting all internal drives during installation.

---

### Post by Uolirod on 2008-01-05
Well, I can give that a try. At least my RAID is SATA so it'll be pretty easy to disconnect. Thanks for the advice.

---

### Post by Pumalite on 2008-01-05
Good luck!

---

### Post by Uolirod on 2008-01-05
No such luck. I disconnected all the hard drives and installed to the external and when I rebooted it still came up error 2.  I may try again tomorrow. Thanks.

---

### Post by Uolirod on 2008-01-06
I booted from the install CD and I get it running using the CD but I still haven't gotten it to boot on its own. :confused:

---

### Post by Pumalite on 2008-01-07
Post:
sudo fdisk -lu (from Live CD)
With USB connected.

---

