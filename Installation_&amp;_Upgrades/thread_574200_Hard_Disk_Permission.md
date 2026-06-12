---
title: "Hard Disk Permission"
date: 2007-10-12
forum: Installation &amp; Upgrades
---

### Post by Dak1n on 2007-10-12
Hi, I have just installed a new hard disk with some files on, and all the permissions are set to root so I cannot change the data on the drive or add any new data.

---

### Post by ryanVickers on 2007-10-12
to view the drive as root, type gksudo nautilus in the terminal and then view the drive ;) - You will be viewing it as root, so you can do anything.  Personally, I think this is a temporary fix because you *should* be trieng to change the entire drive permissions to let 'everyone' see/edit it, but...

---

### Post by ajgreeny on 2007-10-12
The hard drive will presumably show up on ```
sudo fdisk-l
``` as /dev/hdb or something similar.  What you need to do is simply chown the partition when it is mounted in /media/hdb or whatever it is.  You do this with ```
sudo chown -R user:group /media/hdb
```though you may need to change the /media/hdb to whatever you have it mounted as.  The user:group will normally both be your user name.  This will make the disk read/write just by you, but it would be possible to change permissions by changing the /etc/fstab file entry for that disk if it is already in there and mounted automatically.  Have a look at [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html) which may help you in this.

---

