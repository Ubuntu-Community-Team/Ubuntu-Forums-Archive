---
title: "Swap partition not mounting"
date: 2012-04-12
forum: Installation &amp; Upgrades
---

### Post by LeoMcSnarf on 2012-04-12
I need some help with my swap partition. I had Oneiric installed and I upgraded to Precise...
Then I used the livecd to run gparted so I could resize some partitions. I shrunk / (dev/sda1) moved /home left and grew it (dev/sda2) and deleted swap and remade a new swap partition that was smaller (dev/sda3). The / and /home partitions mount fine on boot, however the swap doesn't get automounted... I can use gparted to "swap on" but the next day it didn't automount again. Is there a way I can have the /etc/fstab automatically reinitialized? I'm not real good at config editing... 


here is the contents of /etc/fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=44316aaa-3b49-41c3-9448-e0a6ab45abb6 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=b1e186c1-eb0f-4fb2-b1f4-30640c95fd33 /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=7f315271-123b-4e55-8380-91c77025cbf2 none            swap    sw              0       0

here is the contents of /etc/mtab:

/dev/sda1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
/dev/sda2 /home ext4 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/ben/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=ben 0 0
gvfs-fuse-daemon /root/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev 0 0

and here is the output of cat /etc/fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=44316aaa-3b49-41c3-9448-e0a6ab45abb6 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=b1e186c1-eb0f-4fb2-b1f4-30640c95fd33 /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=7f315271-123b-4e55-8380-91c77025cbf2 none            swap    sw              0       0

---

### Post by coffeecat on 2012-04-12
@LeoMcSnarf, I've moved your post into its own thread as your problem is quite different from the one in the thread you posted to. Please start your own threads unless posting to a megathread.

The answer to your problem is quite straightforward and has two possible solutions - either edit /etc/fstab or reset the UUID on the new swap partition. So that I can help you with this, please post the output of these two terminal commands:

```
sudo fdisk -l
sudo blkid
```

---

### Post by LeoMcSnarf on 2012-04-12
Hey, sorry about posting in the wrong place... I'm just stumbling around in here. Well I think I had figured it out on my own, but if you could hear my fix and tell me if you concur, that would be great. I wasn't too familiar with the UUID for partitions, but I guess that is the way it is done now... I realized that when comparing the UUID that was listed in /etc/fstab it was not the same as the one when I pulled up info on the partition via gparted.... so I edited the /ect/fstab to look for the UUID of the new swap partition and now (so far) it mounts the swap at book. Sound good??? Thanks :)

---

### Post by coffeecat on 2012-04-13
> **LeoMcSnarf said:**
> so I edited the /ect/fstab to look for the UUID of the new swap partition and now (so far) it mounts the swap at book. Sound good??? Thanks :)

Yes, sounds good. That was one of the methods that I referred to. As a matter of information, using Gparted to see the UUID of the swap partition is perfectly OK, but a quicker and simpler way is the "sudo blkid" command I posted. That lists all the UUIDs (and labels if present) for all your partition.

For the record, the other method you could have used is to have run the mkswap command in the terminal with the -U option to set the UUID of the swap partition to the same as was originally in your /etc/fstab file. Either way works.

Good luck!

---

