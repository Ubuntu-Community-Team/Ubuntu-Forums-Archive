---
title: "lucid 64 using lvm grub rescue no such device"
date: 2010-07-01
forum: Installation &amp; Upgrades
---

### Post by eddarl on 2010-07-01
I was using this system until two days ago
The system is intact but when I try to boot 
I get error no such device e7df........
grub rescue>

I have read all the postings I can and have tried to reinstall grub.
it says it has succeeded but I still cannot boot into the system 
normally.
I can use the live cd to mount my system with rescue a broken system but I can't seem to fix grub.

My boot device is sda1
my lvm volume is /dev/ubuntu/root
or /dev/mapper/ubuntu-root

I believe the uuid of lvm volume changed and for the life of me cannot
seem to get grub to see this.
Some help please?

---

### Post by Shadowfire on 2010-08-10
> **eddarl said:**
> 
I believe the uuid of lvm volume changed and for the life of me cannot
seem to get grub to see this.
Some help please?



I am also having issues with my Ubuntu 9.04 64bit server and am working to get it to boot up.  I am not sure if this will help, but check it out below:

[http://linuxwave.blogspot.com/2007/11/mounting-lvm-disk-using-ubuntu-livecd.html](http://linuxwave.blogspot.com/2007/11/mounting-lvm-disk-using-ubuntu-livecd.html)


Thank
SF

---

### Post by Shadowfire on 2010-08-10
Here is another post that may help.

[http://ubuntuforums.org/showthread.php?t=1520447&highlight=lvm+grub+error+15](http://ubuntuforums.org/showthread.php?t=1520447&highlight=lvm+grub+error+15)

Thanks
SF

---

