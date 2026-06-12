---
title: "Update broke my computer"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by matthewboh on 2009-11-13
I ran the latest update for Firefox and xulrunner on my installed 9.10 and the next time I booted, I got the error message

> Gave up waiting for root device.  Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the wrong device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/547309ac-3671-4993-924d-a2b46cbba284 does not exist.  Dropping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [   49.618601] Disabling IRQ#1

So it sounds like it's got the wrong uuid - so I do 

```
blkid
/dev/sda5: UUID="c2a6799e-55ad-467c-a215-f11d40a34c19" TYPE="swap"
```

So I figure the update somehow hosed that UUID, so I boot off a LiveCD, and go to /boot/grub/menu.lst and change the UUID's to the UUID I got from running the blkid

Now it's saying that it can't find /root directory and looks like it's hosed even further.

Any ideas?  I was happily running 9.10 for a week and a half before this happened.

---

### Post by darkod on 2009-11-13
Type=swap means it's the swap file partition, not root. It is normal it won't boot with that uuid.

However, it is very bad that blkid does not show any other partitions on your drive basically. Is it?

PS. If you could boot with live CD you might be able to get a better look at the partitions/drive.

---

### Post by matthewboh on 2009-11-13
I am able to boot up with the LiveCD - I can even use "Places" to browse the drive.  What else should I be looking for?

---

### Post by darkod on 2009-11-13
Open Gparted, select your root partition and click Information from the menu (something like that). Be careful, do not format it. :)
Info in Gparted will show you UUID of the root partition. Use that # in grub menu and see how it goes.

---

### Post by wojox on 2009-11-13
The content of your "/etc/fstab" file.

---

### Post by matthewboh on 2009-11-13
I have a really old LiveCD and the version of gparted on that one doesn't show the UUID, but I did run the scan and check disk.

Here's the contents of my fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=547309ac-3671-4993-924d-a2b46cbba284 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda5
UUID=c2a6799e-55ad-467c-a215-f11d40a34c19 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

---

### Post by matthewboh on 2009-11-13
Just went into /etc/fstab and changed UUID= back to /dev/sda1 (check to make sure you put the right number in) and it rebooted just fine.

Thanks all!

---

