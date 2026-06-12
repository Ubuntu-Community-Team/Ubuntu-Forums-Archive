---
title: "Lost dual-boot to Windows with 9.10 install"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by reedk on 2009-12-05
I'm not new to Linux or Ubuntu, but Karmic with this "beta4" tagged GRUB has my head spinning.

I had a working dual-boot system with XP and 9.04. For a few reasons, I did a fresh install of 9.10 on /dev/sda. The new boot menu did not add my XP partition on /dev/sdb. After some research I've tried adding both of these to /etc/grub.d/40_custom:

First try, which never got to a Windows boot screen:
```
#menuentry "Microsoft Windows XP" {
#        set root=(hd1,1)
#        chainloader +1
#}
```

Second try, which reboots the PC when selected (the UUID is correct for my machine):

```
menuentry "Windows XP" {
insmod ntfs
set root=(hd1,1)
search --no-floppy --fs-uuid --set 78F42836F427F552
chainloader +1
}
```

Here is fdisk -l:
```
Disk /dev/sda: 60.5 GB, 60481863680 bytes
255 heads, 63 sectors/track, 7353 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x83279e15

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        7173    47849602+  83  Linux
/dev/sda3            7174        7353     1445850   82  Linux swap / Solaris

Disk /dev/sdb: 74.4 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x486def14

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sdb2            2551        9039    52122892+  83  Linux
```

And my blkid
```
/dev/sda1: UUID="8091bdf2-6f42-4b5c-b126-92a5c261b213" TYPE="ext4" 
/dev/sda2: UUID="1d6fcf09-556a-4405-825d-6b0870623447" TYPE="ext4" 
/dev/sda3: UUID="88fa0ebe-cbad-48ee-9dd7-5ea731b9748d" TYPE="swap" 
/dev/sdb1: UUID="78F42836F427F552" TYPE="ntfs" 
/dev/sdb2: UUID="57e06483-591e-47e6-960a-753cde3bf561" SEC_TYPE="ext2" TYPE="ext3" 

```

Any thoughts on what I need to do to restore a functional Windows boot to this machine?

---

### Post by phillw on 2009-12-05
Head over here --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Have you up and running in no time :-)

If you're on 9.10 - you're on grub2

Regards,

Phill.

---

### Post by darkod on 2009-12-05
It's a long shot but did you check device.map to make sure hd1 is the one you think it is? Although that doesn't explain why an entry was not created automatically.

---

### Post by reedk on 2009-12-05
Thanks for the help Phil, but the bootloader restore doc doesn't help, becuase I have a working 9.10/grub2 bootloader that gets me into karmic just fine. My problem is that I can't sucessfully boot into the Windows partition.
I did check the device map and it confirms that the devices are named the way I think they are:
```
$more device.map 
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
```
I noticed that running update-grub gives this message about /dev/sdb (My windows drive)
```
ERROR: isw device for volume "REYES" broken on /dev/sdb in RAID set "isw_eabdghgdbd_REYES"
ERROR: isw: wrong # of devices in RAID set "isw_eabdghgdbd_REYES" [1/2] on /dev/sdb

```
This is odd because I've _never_ had RAID set up on this drive and the REYES naming is not something of my creation. Alas, Google is not helping me here :(

---

### Post by darkod on 2009-12-05
But
sudo apt-get remove dmraid

should help you. :) Execute that and it will remove any raid leftovers from the system. I know, seems confusing but it seems some drives can sometimes come with raid leftovers that you know nothing about.

---

### Post by reedk on 2009-12-06
Darko, you nailed it. removing dmraid allowed GRUB to auto-add a Windows entry. That drive must have lived in my storage server at one time. I'll move this to solved and scan the forums to see if I can help anyone else with the same problem.
Thanks again all for the responses.

---

