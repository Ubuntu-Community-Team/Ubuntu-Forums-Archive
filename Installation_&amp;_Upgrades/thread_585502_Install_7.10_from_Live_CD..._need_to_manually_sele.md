---
title: "Install 7.10 from Live CD... need to manually select partition... how do I do this?"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by Robotman on 2007-10-21
In response to [this]("http://ubuntuforums.org/showthread.php?p=3591223#post3591223") problem, I've decided to just install Ubuntu 7.10 from scratch over my existing Ubuntu partition.
I've hit an impasse though.  I need to install Ubuntu on the partition sda2.  However, the Ubuntu installer wants to partition sdb.  I must choose the "Manual" option in the "Prepare disk space" part of the install process.
The next step confuses me.  I select "/dev/sda2" as the partition to prepare, but when I click "Forward", I get an error message:
```
No root file system is defined.
Please correct this from the partitioning menu.
``` 
How do I do this?  The sda2 partition shows as being Type=ext3, Mount point=/media/sda2.  There is also a swap partition at /dev/sda5 from the previous Ubuntu installation.
How can I specify the root file system and continue with the installation?

---

### Post by Jimlas53 on 2007-10-21
If you edit the mount point, you set it to /.
In your case, sda2 is currently mounted at /media/sda2, and you need to change its mount point to /, which is the root. Your swap is fine and will work with both installations.
Remember to also select "format" for your new sda2 root partition.

Hope this helps!

-Doug

---

### Post by skompier on 2007-10-21
On the screen that shows your partition information, there is a box under it that reads "Mount Point" or something similar. Place a / in it before you hit next.

---

