---
title: "Quad Boot"
date: 2012-01-15
forum: Installation &amp; Upgrades
---

### Post by psmokashi on 2012-01-15
Hi,

My config as follows:

1st HDD: C: First partion has Win 7 32 bit
1st HDD: D: Second partition has Win 7 64 bit

1st HDD is 500 GB split into two equal partitions.

2nd HDD is 500 GB

2nd HDD is split as follows:  E: 250 GB NTFS
                                                   100 GB Unallocated
                                                   150 has SUSE 12.1
I have Acronis OS installed on Win 7 32 bit partition.
Suse's Grub is not installed on Win partitions. Grub is on Suse's
partition. 

I want to instal  Ubuntu on the second HDD in the unallocated space. Ubuntus loader should be only installed on Ubuntus partition only. Windows MBR should not be over written. Please advise. Regards, Prashant:confused:

---

### Post by darkod on 2012-01-15
Grub2 is not recommended to be installed on a PBR. It doesn't fit all on the PBR so it has to put part of it inside the partition. During updates this location can change or something, making grub2 to break.

You could install grub2 to the MBR of sdb and you would still have windows bootloader on the MBR of sda.

But if you still want grub2 on the ubuntu partition, you need to:
Start the instal and select Something Else (manual install).
Into the 100GB unallocated space create the ubuntu partition(s) you need.
Under the partitions list there is a drop-down box to select where to install grub2. Just select the ubuntu partition.
That's it.

---

### Post by psmokashi on 2012-01-15
> **darkod said:**
> Grub2 is not recommended to be installed on a PBR. It doesn't fit all on the PBR so it has to put part of it inside the partition. During updates this location can change or something, making grub2 to break.

You could install grub2 to the MBR of sdb and you would still have windows bootloader on the MBR of sda.

But if you still want grub2 on the ubuntu partition, you need to:
Start the instal and select Something Else (manual install).
Into the 100GB unallocated space create the ubuntu partition(s) you need.
Under the partitions list there is a drop-down box to select where to install grub2. Just select the ubuntu partition.
That's it.

Hi, Tks for ur prompt response.
I am a noobe as regards to Linux!
I did some how manage to install Suse.
Can u please guide where can i find a step by step guide?

---

### Post by darkod on 2012-01-15
I don't know Suse much, but I think it still uses the older grub1. grub1 is smaller and can fit on the PBR without a problem. With grub2, there are problems, if not immediately, then down the line.

I guess you already have a swap partition on the second disk (/dev/sdb) which is used for suse. Linux can use the same swap partition for more distributions, because you have only one booted at the same time anyway.

This is one guide with screenshots I found quickly:
[http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide](http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide)

The latest version might look slightly different but it's the same thing you need to do. As mentioned above, if you already have one swap area partition you need to create just the main, root partition for ubuntu. And to make sure you install grub2 to the same disk. If it's /dev/sdb, then you need to install grub2 to /dev/sdb (without any number in it).

---

### Post by psmokashi on 2012-01-15
> **darkod said:**
> I don't know Suse much, but I think it still uses the older grub1. grub1 is smaller and can fit on the PBR without a problem. With grub2, there are problems, if not immediately, then down the line.

I guess you already have a swap partition on the second disk (/dev/sdb) which is used for suse. Linux can use the same swap partition for more distributions, because you have only one booted at the same time anyway.

This is one guide with screenshots I found quickly:
[http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide](http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide)

The latest version might look slightly different but it's the same thing you need to do. As mentioned above, if you already have one swap area partition you need to create just the main, root partition for ubuntu. And to make sure you install grub2 to the same disk. If it's /dev/sdb, then you need to install grub2 to /dev/sdb (without any number in it).

Tks for the lnk. I have the following sp problems1) how many partitions2)/ or boot ?3) type ext 4 exr 2? 4) size of partitiins?5)where to put the boot loader in terms of which partition?6)new version has lots of input requirements when u select manual instal!!! Sorry for tooo many questions

---

### Post by darkod on 2012-01-15
No, there are not too many input questions :)

The partition size can be the whole unallocated space. Make it primary type if it allows you. The mount point is /. Filesystem ext4.

That's it.

The bootloader goes on the same disk, so if the new partition is for example /dev/sdb4, then put the bootloader on /dev/sdb (without the number). The number labels the partition, and the letter after 'sd' labels the disk.
Put it on the same disk where the / partition is.

---

### Post by psmokashi on 2012-01-15
> **darkod said:**
> No, there are not too many input questions :)

The partition size can be the whole unallocated space. Make it primary type if it allows you. The mount point is /. Filesystem ext4.

That's it.

The bootloader goes on the same disk, so if the new partition is for example /dev/sdb4, then put the bootloader on /dev/sdb (without the number). The number labels the partition, and the letter after 'sd' labels the disk.
Put it on the same disk where the / partition is.

tks will try n report back

---

### Post by psmokashi on 2012-01-16
> **psmokashi said:**
> tks will try n report back

Hi,

I tried....but failed :(((((

Should the setting be.....Primary - Begining - Ext 2 ../boot
                          Logical - SWAP
                   (Root) Logical - Begining or End? - Ext 4.../
                          Logical - Begining or End? - Ext4.../home                         

I do not wish Ubuntu to use any Suse SWAP area etc.

---

### Post by psmokashi on 2012-01-19
> **psmokashi said:**
> Hi,

I tried....but failed :(((((

Should the setting be.....Primary - Begining - Ext 2 ../boot
                          Logical - SWAP
                   (Root) Logical - Begining or End? - Ext 4.../
                          Logical - Begining or End? - Ext4.../home                         

I do not wish Ubuntu to use any Suse SWAP area etc.

Some how it has worked....tks

---

