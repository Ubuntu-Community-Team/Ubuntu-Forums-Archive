---
title: "Can't boot to a specific drive when using identically partitioned drives"
date: 2022-12-09
forum: Installation &amp; Upgrades
---

### Post by robertcull1 on 2022-12-09
I am using a ThinkPad T430 with three drives: a SATA drive that boots Windows 7 and 10, an mSATA drive, and another SATA drive which fits into an UltraBay SATA drive enclosure which can be easily removed from the system. 


Normally I run the operating system out of the / and /home directories on the UltraBay drive. I choose to take out the UltraBay drive out of the system and take with me when I go out.


Before leaving I backup the UltraBay drive to the mSATA drive. If someone were to alter the mSATA drive I leave in the system in my absence, I would have the original UltraBay drive in my pocket without any alterations.


Once a month I copy the partitions from the UltraBay drive to the mSATA drive and make the mSATA drive bootable. Rather than copy the partitions every time I go out--the time it would take would be prohibitive--I sync the UltraBay drive to the mSATA drive using rsync at the command line. This takes very little time, only replacing those files that have been modified.


To test if the mSATA drive is bootable, I boot the system without the UltraBay drive from the mSATA drive. This way I know everything is fine, if I lose the UltraBay drive.


So far, to make sure all the drives will boot, I take all but one of the drives out at a time and use boot-repair on them individually from a bootable Ubuntu thumb drive. When any one of these drives are in the system, it will boot from that drive.


When I get back home, the system is still running from the mSATA drive. I reinsert the UltraBay drive--leaving the mSATA drive in--and reboot. I use the F12 key to choose to boot from the UltraBay drive.


I would expect that would cause the system to boot from the UltraBay drive. But to my surprise, it causes it to boot from the mSATA drive.


Can someone please tell me how to make it boot from the UltraBay drive?

---

### Post by oldfred on 2022-12-09
Is your sync too good & includes duplicate UUIDs. That is not allowed.
Some that have had duplicate UUIDs and reboot, find UEFI/BIOS may boot one drive one time and the other next time. And then systems get totally out of sync. 

post this with all drives plugged in:
lsblkt -f

---

### Post by robertcull1 on 2022-12-10
```
$ lsblk -f
NAME FSTYPE LABEL UUID MOUNTPOINT

sda
&#9500;&#9472;sda1 ext4 5a369ba6-efec-46dc-b265-dc7ee36ff038 /boot
&#9500;&#9472;sda2 ext4 c8084614-833d-4f44-80f0-2b34f31e6f4e
&#9500;&#9472;sda3 ext4 83e8b16b-400a-474e-aa7e-9893d6e34ab6
&#9492;&#9472;sda4 ext4 Extra c2c86959-d870-44a6-9c00-8a701f24cdb5
sdb
&#9500;&#9472;sdb1 ext4 5a369ba6-efec-46dc-b265-dc7ee36ff038
&#9500;&#9472;sdb2 ext4 c8084614-833d-4f44-80f0-2b34f31e6f4e /
&#9500;&#9472;sdb3 ext4 83e8b16b-400a-474e-aa7e-9893d6e34ab6 /home
&#9492;&#9472;sdb4 ext4 Extra c2c86959-d870-44a6-9c00-8a701f24cdb5
```

---

### Post by oldfred on 2022-12-10
Duplicate UUIDs.
Your UEFI/BIOS may randomly boot one drive or the other, depending on which drive is seen first. If one SSD, it may normally be seen first, but not guaranteed.

Better to have separate installs & sync data.
You can change UUIDs on one drive or the other but if you want it to boot, you have to reinstall grub.

---

### Post by robertcull1 on 2022-12-11
I changed the UUIDs with tune2fs and now it works great.

Thanks!

---

