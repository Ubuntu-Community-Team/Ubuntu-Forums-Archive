---
title: "Grub (or MBR) problem"
date: 2011-09-18
forum: Installation &amp; Upgrades
---

### Post by celer on 2011-09-18
Hey!

Having some troubles with new laptop. Installed Ubuntu, which is still working fine... Then installed Windows 7 as dual boot which couldn't catch wifi nor let me play any of the games i remembered from back in the day. Installed XP instead and lost the grub menu. Tried to restore the grub with [Boot-repair](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) which indeed restored the grub to a state where i can boot to ubuntu, but which corrupted the MBR. 

Boot-repair log shows all my partitions: [http://paste.ubuntu.com/692113/](http://paste.ubuntu.com/692113/)
but gparted (in both my installed ubuntu and the live cd) shows this:
[img]http://www.upload.ee/image/1667114/unpartitioned.png[/img]

I can't access any other partitions and am afraid that re-installing (format) wouldn't work.
What can i do?

---

### Post by mörgæs on 2011-09-18
Windows does not play nicely with other operative systems. Best is to install Windows first, leaving empty space and then install Ubuntu.

---

### Post by YesWeCan on 2011-09-18
Your MBR partition table is indeed corrupted. You have a primary partition, sda4, overlapping with your extended partition container, sda3.

```
Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848    55,171,071    54,964,224   7 NTFS / exFAT / HPFS
/dev/sda3          55,175,166   [COLOR="Red"]976,771,071[/COLOR]   921,595,906   5 Extended
Extended partition linking to another extended partition.
/dev/sda5          55,175,168   874,375,167   819,200,000   7 NTFS / exFAT / HPFS
/dev/sda6         874,377,216   968,800,255    94,423,040  83 Linux
/dev/sda4         [COLOR="red"]968,800,256   976,771,071[/COLOR]     7,970,816  82 Linux swap / Solaris

[COLOR="red"]/dev/sda3 overlaps with /dev/sda4[/COLOR]
```

I think the easiest way out of this is to delete sda4 (the swap partition) and then GParted will start working and you can make a new, logical swap partition in the unallocated space inside the extended partition.

To delete the sda4 entry in the MBR partition table of sda:
```
sudo dd if=/dev/zero of=/dev/sda bs=1 count=16 seek=494
```
Be very careful to copy this exactly or you could lose access to all the data on the disk.

---

### Post by celer on 2011-09-18
It worked!

I have to mount partitions manually now but at least i can get access to them until 11.10 and a complete format.

Thank you!

---

### Post by YesWeCan on 2011-09-18
Pleasure. :)
Don't forget to mark this solved in [COLOR="Red"]Thread Tools[/COLOR] when you are ready.
You wrote:
> Tried to restore the grub with Boot-repair which indeed restored the grub to a state where i can boot to ubuntu, but which corrupted the MBR. 
Are you sure that the GParted problems started after you used Boot-repair? It is just that if there is a problem with Boot-repair we (or someone) needs to be made aware of it and fix it.

---

### Post by psrdotcom on 2011-09-18
Please mark this as solved .. Thanks

---

