---
title: "Where the heck is my boot partition? New install won't boot!"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by MountainX on 2008-07-24
I'm not sure why my new 8.4.1-server intall will not boot. I think my /boot partition can't be found.

I have four identical hard drives on one controller (LSI MegaRAID 320-2E). I created a /boot partition (unencrypted) on one drive during install. I also created a / partition (encrypted) on that drive. So that drive has 2 paritions. I created one partition on each of the other drives. Then I completed installation and rebooted. (Many times.) No boot. No error message. Only a blank screen and a blinking cursor.

I burned Super Grub Disk. It shows 4 partitions (not the 5 that I created). All are the same size. Where did my /boot partition go? (I have other disks on another controller... but that is actually unplugged at the moment for troubleshooting.)

What to do? Re-install? Well I've been trying that for 3 days, so I need new ideas or suggestions. Thanks.

---

### Post by MountainX on 2008-07-24
I removed all my HDD's except one and I made that one a passthrough drive. Then I installed as before except that I didn't make a separate /boot partition. The install was successful.

Now I just have to figure out how to get the install to work when using multiple drives. I will have /home, /tmp, /var and swap on different spindles. /boot will be a separate partition because of encryption.

Any ideas about what my prior problem could be? As soon as I attempt an installation with a separate boot partition and/or multiple drives, I get the problem mentioned in this thread.

---

### Post by wpshooter on 2008-07-24
If you are using the "manual" partitioning procedure, are you coming down to the "**BOOTABLE**" parameter (I think it is very near the end of the listing of partition parameters) when you create the /root partition and making it **BOOTABLE** ?

---

### Post by MountainX on 2008-07-24
> **wpshooter said:**
> If you are using the "manual" partitioning procedure, are you coming down to the "**BOOTABLE**" parameter (I think it is very near the end of the listing of partition parameters) when you create the /root partition and making it **BOOTABLE** ?

Yes, I'm doing the manual partitioning. I am setting the bootable flag to "ON".

---

### Post by MountainX on 2008-07-31
SOLVED

See this post:
[http://www.backports.ubuntuforums.org/showthread.php?p=5499285#post5499285](http://www.backports.ubuntuforums.org/showthread.php?p=5499285#post5499285)

---

