---
title: "Multiple Swap Partitions"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by BrockStrongo on 2011-05-02
Hi everyone,
    After reverting back to 10.04 from 11.04 I noticed I have an additional swap partition.
I would like to format one of these if they are not needed.

Here is the result of swapon -s

```
Filename                Type        Size    Used    Priority
/dev/sda4                               partition    4056056    0    -1
/dev/sda5                               partition    11489272    0    -2
```


here is the result of  sudo fdisk -l
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00072518

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       20036   160937984   83  Linux
/dev/sda2   *       20542       37482   136078582+   7  HPFS/NTFS
/dev/sda3           37483       38914    11489281    5  Extended
/dev/sda4           20036       20541     4056064   82  Linux swap / Solaris
/dev/sda5           37483       38914    11489280   82  Linux swap / Solaris

Partition table entries are not in disk order
```

any help is greatly appreciated

---

### Post by Dutch70 on 2011-05-02
First, how much physical RAM do you have?

---

### Post by wojox on 2011-05-02
Boot a live-cd, open gparted. Turn swap off and delete the extended and swap partition.

---

### Post by BrockStrongo on 2011-05-02
I have 4 gigs of RAM.
Thanks

---

### Post by BrockStrongo on 2011-05-02
> **wojox said:**
> Boot a live-cd, open gparted. Turn swap off and delete the extended and swap partition.


Thanks.

 Just for clarification, do you mean turn off the swap using G-Parted?
  ie; right click on partition, =====> swapoff?
Thanks

---

### Post by Dutch70 on 2011-05-02
If you don't need to hibernate, you can do as wojox said, but I don't know what you'll do with the 11GB of unallocated space it will leave you. Although there are a few things you could do with it.

If you do need to hibernate, you'll need at least 4GB of swap. Having just a tad bit more is a good idea. So doing the above won't allow you to hibernate successfully & you may be better off to keep the larger one.

Edit: yes that's what he means.

---

### Post by BrockStrongo on 2011-05-02
> **Dutch70 said:**
> If you don't need to hibernate, you can do as wojox said, but I don't know what you'll do with the 11GB of unallocated space it will leave you. Although there are a few things you could do with it.

If you do need to hibernate, you'll need at least 4GB of swap. Having just a tad bit more is a good idea. So doing the above won't allow you to hibernate successfully & you may be better off to keep the larger one.

Edit: yes that's what he means.


Could I delete the 3.87 gig partition and extend the ext4 partition? 
Then use the 10.96 Gb partition as swap?
Thanks again.

---

### Post by Dutch70 on 2011-05-02
I don't see any problem with that at all. 

You may need to edit fstab so it won't continue to try and mount the partition on reboot, but that's easy enough to do.

After you delete the swap prtn, post the output of...
```
gksudo gedit /etc/fstab
```

---

### Post by BrockStrongo on 2011-05-02
> **Dutch70 said:**
> I don't see any problem with that at all. 

You may need to edit fstab so it won't continue to try and mount the partition on reboot, but that's easy enough to do.

After you delete the swap prtn, post the output of...
```
gksudo gedit /etc/fstab
```


Deleting went fine here is the output of...
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=25112173-badb-4472-b8ba-7e22cf1e5c66 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=658136f3-c8c8-4a63-ad45-e4db6a7a05ff none            swap    sw              0       0
# swap was on /dev/sda5 during installation
UUID=71b6a224-83c7-4ecd-ae9a-841bdc73b181 none            swap    sw              0       0{7
```

Could I shrink the other swap to something like 6 Gb?  (4 Gb RAM)
Thanks for all your help :)

---

### Post by Dutch70 on 2011-05-02
You can delete the part in red & click "save".

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=25112173-badb-4472-b8ba-7e22cf1e5c66 /               ext4    errors=remount-ro 0       1
[COLOR="Red"]# swap was on /dev/sda4 during installation
UUID=658136f3-c8c8-4a63-ad45-e4db6a7a05ff none            swap    sw              0       0[/COLOR]
# swap was on /dev/sda5 during installation
UUID=71b6a224-83c7-4ecd-ae9a-841bdc73b181 none            swap    sw              0 
```

Yes you can shrink your swap partition to about 4 - 4.5 GB to be safe. Then create a new partition for extra storage. 
If you format it to NTFS, you can share it with windows or use it to transfer files between windows & Ubuntu.

Or format it to ext3 and install fs-driver into windows so that it can read ext3 file systems.

---

### Post by BrockStrongo on 2011-05-03
Problem Solved. Thank you very much for your expertise. Your help is greatly appreciated.

Cheers

---

### Post by Dutch70 on 2011-05-03
You're welcome. Glad you got it worked out.

---

