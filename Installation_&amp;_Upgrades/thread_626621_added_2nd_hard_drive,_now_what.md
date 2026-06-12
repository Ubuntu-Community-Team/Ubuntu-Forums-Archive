---
title: "added 2nd hard drive, now what?"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by jpl80 on 2007-11-29
I added a 2nd hard drive. Now I'm confused. I want to use the 2nd hard drive seamlessly with the 1st hard drive. I don't want to go to /media/disk/ every time I want to save/open something. Is there a way to do that?

right now, /dev/sda holds the MBR and everything else. I want to format the 2nd hard drive (/dev/sdb) and "give it" to /dev/sda

here is the output from fdisk -l

$ sudo fdisk -l

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4791    38483676   83  Linux
/dev/sda2            4792        4998     1662727+   5  Extended
/dev/sda5            4792        4998     1662696   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7f45f172

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4678    37576003+  83  Linux
/dev/sdb2            4679        4865     1502077+   5  Extended
/dev/sdb5            4679        4865     1502046   82  Linux swap / Solaris

---

### Post by jpl80 on 2007-11-29
Perhaps I could just purchase a big 250 GB drive and move everything over?

Any ideas?

---

### Post by jpl80 on 2007-11-29
found some excellent instructions here:

[http://www.smorgasbord.net/2007/06/29/how-to-install-second-hard-drive-in-ubuntu-linux/](http://www.smorgasbord.net/2007/06/29/how-to-install-second-hard-drive-in-ubuntu-linux/)

I will try it as soon as I get home.

---

### Post by confused57 on 2007-11-29
Here are 2 excellent guides for mounting linux partitions:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_a_reiserfs_filesystem](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_a_reiserfs_filesystem)

I have 2 large data partitions on 2 other separate hard drives from the hd that my main OS is on... I have them mounted as /media/data and /media/data2...both of which have icons on the desktop, that I can click on to access. 

I'm not sure if this helps any...I can give you a little more detail, if you think this is what you want.

---

### Post by jpl80 on 2007-11-30
Yes that helps, I mounted the drive and everything works fine. I think I'll just create a link from my home folder to the new drive.

---

