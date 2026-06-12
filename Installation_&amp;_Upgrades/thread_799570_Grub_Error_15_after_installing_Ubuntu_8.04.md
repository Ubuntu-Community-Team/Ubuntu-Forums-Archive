---
title: "Grub Error 15 after installing Ubuntu 8.04"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by AtliThor on 2008-05-19
Hi.

I've been trying to install Ubuntu 8.04 all night. I have 3 HDD's, partitioned 5 ways, 4 of which are formatted NTFS and the last is just 40GB of unpartitioned spaces I intend to use for my Ubuntu installation.

First I tried Kubuntu, but after the install had completed and I had restarted, my computer didn't find any bootable drives.
I tried again with Ubuntu but the same thing happened.

So... I tried with Kubuntu 7.04 which worked perfectly... but I still want 8.04 :P

Now, during my 5'th(ish) attempt, I created my partitions manually. Creating one for swap, a second for /boot and a third for the root.

And what do you know... I finally get a GRUB loading screen, only to have it fail, showing "Error 15", which I understand to be some sort of a "File not found" error?

Any input would be appreciated.
Thanks.

---

### Post by housam on 2008-05-19
Try to [[COLOR="Red"]_reinstall grub _[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?#head-778ecd20f83f92ebaa5aaec5f1b4615539c2f8d3")

but first boot from ubuntu live CD and type in a terminal 
```
sudo fdisk -l 
```
where -l is a small L and post the results

---

### Post by AtliThor on 2008-05-19
Hi. Thanks for the quick reply.

The output of the fdisk -l command is:
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa0d200dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641   42  SFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x63829f30

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            5223       24320   153404685    f  W95 Ext'd (LBA)
/dev/sdb2               1          61      489951   83  Linux
/dev/sdb3              62         304     1951897+  82  Linux swap / Solaris
/dev/sdb4             305        5222    39503835   83  Linux
/dev/sdb5            5223       24320   153404653+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe6fdb063

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2        3916    31447237+   f  W95 Ext'd (LBA)
/dev/sdc2   *        3917       24321   163903162+   7  HPFS/NTFS
/dev/sdc5               2        3916    31447206    7  HPFS/NTFS

```
Where /dev/sdb2 is the boot partition and /dev/sdb4 the root partition.

Going to try re-installing GRUB now.

Thanks.

---

### Post by AtliThor on 2008-05-19
Ok, the automatic recovery described in the link you provided appears to have worked... up to a point ^^

GRUB now gives me a list of items to select from, after which I get a "Error 17: Cannot mount selected partition" message.

EDIT: 
I've figured it out!
For some reason GRUB shuffles the HDD's around after it boots, putting the 320GB HDD at /dev/sda(hd0) and the one with the Linux partitions at /dev/sdb(hd1)
During the boot, however, the HDD at /dev/sdb is listed as /dev/sda(hd0), making the menu.lst created by the installer and recovery program after the boot incorrect.

Not sure why that would happen tho.

---

### Post by housam on 2008-05-19
Try the manual way and take care about partition numbering.

---

### Post by AtliThor on 2008-05-19
It seems to be working fine now.
I edited the entries in the menu.lst file to open the (hd0,1) partition and now it all starts up fine.

Thanks for the help.

---

