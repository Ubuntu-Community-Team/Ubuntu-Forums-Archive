---
title: "Reinstall Ubuntu SAFELY"
date: 2010-07-09
forum: Installation &amp; Upgrades
---

### Post by mohitd2000 on 2010-07-09
I have had a previous incident with GRUB and Ubuntu, where I installed Ubuntu on a partition on an externally hard drive and GRUB wouldn't boot unless the external hard drive was connected to my laptop. So my first experience with Ubuntu staggered a little. My second experience (I removed GRUB and installed Ubuntu on a partition on my laptop) was more delightful, until the Ubuntu 10.04 LTS upgrade came. While it was downloading the packages, my router turned off, so my version of Ubuntu I have now is corrupt. Would it be safe to boot into Windows 7, delete the partition, boot from the Ubuntu CD and install it on the same partition as the previously deleted Ubuntu? Will GRUB let me boot without ANY error? Or do I need to delete the partition GRUB is on then remove GRUB via Recovery CD?

---

### Post by dino99 on 2010-07-09
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by mohitd2000 on 2010-07-12
I have 4 partitions. One for Windows, one for recovery, one for ubuntu, and a 510MB one for GRUB (At least I THINK it's GRUB?). So which partitions could I delete and which partitions should I not touch? I am definitely not going to modify my windows or recovery partition. But if the Ubuntu 10.04 installation overwrites GRUB then, can I delete the partitions for ubuntu and grub? Or should I just delete the ubuntu partition. Remember, I don't want this blowing up in my face. I don't have a Windows 7 recovery disc handy (I am in another country to see my relatives and I forgot to bring the recovery disc).

---

### Post by kansasnoob on 2010-07-12
Are you able to boot Ubuntu at all?

If not you can also use an Ubuntu Live CD and post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

From that we should be able to see exactly what your partition arrangement is. Or a screenshot of Gparted would even help. Or, at an absolute minimum, the output of:

```
sudo fdisk -l
```

---

### Post by mohitd2000 on 2010-07-12
> **kansasnoob said:**
> Are you able to boot Ubuntu at all?

If not you can also use an Ubuntu Live CD and post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

From that we should be able to see exactly what your partition arrangement is. Or a screenshot of Gparted would even help. Or, at an absolute minimum, the output of:

```
sudo fdisk -l
```
[IMG]http://i31.tinypic.com/14w3p4w.jpg[/IMG]Is that proficient information? I am able to boot into Ubuntu 9.10 and the newly burned CD with Ubuntu 10.04.

---

### Post by kansasnoob on 2010-07-12
> I am able to boot into Ubuntu 9.10

Then please boot into it and post the output of the following commands:

```
sudo parted /dev/sda print
```

```
cat /etc/fstab
```

---

### Post by mohitd2000 on 2010-07-12
Here is the output (first is sudo parted /dev/sda print, second is cat /etc/fstab):
```
Model: ATA Hitachi HTS54161 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  1574MB  1573MB  primary   ntfs
 2      1574MB  108GB   107GB   primary   ntfs            boot
 3      108GB   120GB   11.5GB  extended
 5      108GB   119GB   11.0GB  logical   ext4
 6      119GB   120GB   535MB   logical   linux-swap(v1)

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=818d65bb-e484-4ec1-9d1e-eb56e0971057 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=19495542-0021-4fa5-9984-bcf9af271561 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by kansasnoob on 2010-07-12
Aha! You see Windows can't be trusted to read Linux partitions properly:

> 1      1049kB  1574MB  1573MB  primary   ntfs
 2      1574MB  108GB   107GB   primary   ntfs            boot
 3      108GB   120GB   11.5GB  **[COLOR="Red"]extended[/COLOR]**
 5      108GB   119GB   11.0GB  **[COLOR="Red"]logical[/COLOR]**   ext4
 6      119GB   120GB   535MB   **[COLOR="Red"]logical[/COLOR]**   linux-swap(v1)


The two Ubuntu partitions (/ and SWAP) are logical partitions even though Windows said they were primary :)

One more question, do you know how much RAM you have?

---

### Post by mohitd2000 on 2010-07-12
> **kansasnoob said:**
> One more question, do you know how much RAM you have? 
I have about 2GB. Plenty to upgrade to Ubuntu 10.04. So what partitions should be deleted? The / and SWAP?

---

### Post by kansasnoob on 2010-07-13
The reason I asked about RAM was because of the SWAP size. Generally SWAP should be slightly larger than total RAM in order for "suspend" and/or "hibernate" to work properly. So, it's up to you, but if I had 2GB of RAM I'd want slightly more than 2GB of SWAP if I ever hope to use suspend or hibernate.

As far as deleting partitions I would NOT use the Windows utility to do so since it doesn't even properly identify the extended partition and the two logical partitions contained therein. I would use Gparted from a Live CD to deal with Linux partitions, **but you should always use Windows own utility to resize Windows partitions!** I prefer this basic method of creating/changing my Linux partitions prior to installing/reinstalling Ubuntu:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

Although you don't need a separate grub partition as shown there! Let's assume you're happy with the size of your SWAP just as an example. In that case you really don't need to delete any partitions, you'd just select "Specify partitions manually (advanced)" from the partitioning screen as shown here:

[http://members.iinet.net.au/%7Eherman546/p22/027.png](http://members.iinet.net.au/%7Eherman546/p22/027.png)

Then you'd select partition /dev/sda5 since that is your root "/" partition as shown here:

[http://members.iinet.net.au/%7Eherman546/p22/031.png](http://members.iinet.net.au/%7Eherman546/p22/031.png)

Choose to accept the default size, select ext4 (or ext3) as "Use as", click on "format", and be sure to set the "mount point" as "/" which is the symbol for "root".

You need do nothing with SWAP, the installer should just automatically choose to use whatever SWAP is available.

Is that fairly clear? Please ask more questions if I've only puzzled you more. Pre-planning is well worth the pain :)

---

### Post by mohitd2000 on 2010-07-13
Thanks a lot. That cleared it up **VERY** much :D.

---

