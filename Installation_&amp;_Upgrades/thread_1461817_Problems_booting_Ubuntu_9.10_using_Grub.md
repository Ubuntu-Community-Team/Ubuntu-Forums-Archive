---
title: "Problems booting Ubuntu 9.10 using Grub"
date: 2010-04-24
forum: Installation &amp; Upgrades
---

### Post by skotu on 2010-04-24
I'm having trouble booting into Ubuntu 9.10 using Grub.

I have two harddrives. First one is the main OS running Xubuntu 8.10. I wanted to try Ubuntu 9.10, so I installed it on the second harddrive but did NOT install the Grub2 bootloader at the last step of the install (so that it wouldn't overwrite Grub).
```
$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x70fd70fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9543    76654116   83  Linux
/dev/sda2            9544        9729     1494045    5  Extended
/dev/sda5            9544        9729     1494013+  82  Linux swap / Solaris

Disk /dev/sdb: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002ce89

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         977     7847721   83  Linux
/dev/sdb2             978        1027      401625    5  Extended
/dev/sdb5             978        1027      401593+  82  Linux swap / Solaris

```

I found the UUID for the second drive by doing:
```
$ sudo blkid
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="c82bb269-3501-473e-a916-33390a8d85f6" TYPE="ext3"
/dev/sda5: UUID="c9a77c88-a0bc-422c-bf93-8ddb00c525e5" TYPE="swap"
/dev/sdb1: UUID="bb616b6a-c2ac-4a57-903d-9a70ef11f0c0" TYPE="ext4"
/dev/sdb5: UUID="84942b0c-47e0-4fcf-a8bd-16a241c7d5cf" TYPE="swap" 
```

Then I edited the /boot/grub/menu.lst file and added the following section at the end:
```
title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        bb616b6a-c2ac-4a57-903d-9a70ef11f0c0
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=bb616b6a-c2ac-4a57-903d-9a70ef11f0c0 ro splash quiet
initrd        /boot/initrd.img-2.6.31-14-generic
quiet
```

When I boot up and select this entry from the Grub menu, it shows the following info but never boots into the OS:
```
Boot from (hd1,0) ext4 bb616b6a-c2ac-4a57-903d-9a70ef11f0c0
```

What am I missing?

Thanks.

---

### Post by skotu on 2010-05-01
Never got it figured out. Ended up installing 9.10 on the second drive and letting it install grub2 to the MBR of the first drive.

---

### Post by oldfred on 2010-05-01
Just for info or if anyone else looks at this since you have already reinstalled.
Old grub had to be updated to see ext4 partitions. That update was in 9.04 so your version of grub legacy was not compatible with ext4 partitions. Since you have two drives you could have installed grub 2 the the second drive and just chainbooted to it.

---

### Post by malrost on 2010-05-01
> **oldfred said:**
> Just for info or if anyone else looks at this since you have already reinstalled.
Old grub had to be updated to see ext4 partitions. That update was in 9.04 so your version of grub legacy was not compatible with ext4 partitions. Since you have two drives you could have installed grub 2 the the second drive and just chainbooted to it.

Interesting. I would have thought it was simply because he didn't have "boot" as the last line of his menu.lst entry.

---

