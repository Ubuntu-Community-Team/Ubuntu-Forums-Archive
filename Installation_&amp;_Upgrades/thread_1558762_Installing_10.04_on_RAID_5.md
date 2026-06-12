---
title: "Installing 10.04 on RAID 5"
date: 2010-08-22
forum: Installation &amp; Upgrades
---

### Post by Gralamin on 2010-08-22
I have a computer set up in RAID 5 (Using an Intel Controller on my Motherboard), dual-booting Windows 7 and XP. I've created a partition to add Ubuntu in, as I've done on Non-RAID machines.  (Using DVD to ensure all install options available)

I have a RAID table that looks like this:

```

/dev/mapper/isw_cecafgaibc_Volume0
   /dev/mapper/isw_cecafgaibc_Volume01  NTFS 226021 MB, Unknown Used
   Free space                                106374 MB,
   /dev/mapper/isw_cecafgaibc_Volume05  NTFS 657150 MB, Unknown
   /dev/mapper/isw_cecafgaibc_Volume06  NTFS 9646 MB, unknown

```
I wish to add a 97374 logical at the beginning with type ext4 and mount of /, as well as an 10000 logical at end with type swap.(Volume 7/8 respectively)

It is able to create the swap without problem, but attempting to make the ext4 fails.

Help?

---

### Post by ronparent on 2010-08-22
It appears that you already have three primary ntfs partitions, two separated by unallocated space from the first one. Although Win 7 might allow you to create a partition in that space I'm not certain that Ubuntu would if it were an extended one. Basically you only have the capability left to create one extended partition without exceeding a limitation of a total of four primary partitions including an extended partition. Since ubuntu can be installed anywhere, you would probably have been better of to have created your ntfs partition contiguously. But once you have created your extended partition you will be free to create as many and whatever types of logical partition you may want. Post if you have more questions.

---

### Post by Gralamin on 2010-08-22
> **ronparent said:**
> It appears that you already have three primary ntfs partitions, two separated by unallocated space from the first one. Although Win 7 might allow you to create a partition in that space I'm not certain that Ubuntu would if it were an extended one. Basically you only have the capability left to create one extended partition without exceeding a limitation of a total of four primary partitions including an extended partition. Since ubuntu can be installed anywhere, you would probably have been better of to have created your ntfs partition contiguously. But once you have created your extended partition you will be free to create as many and whatever types of logical partition you may want. Post if you have more questions.

Not the problem - I'm creating a logical partition, for each, and beside, if I remove the swap and try to make the ext4 only, it still fails.

Edit: The windows SWAP is also part of an extended partition.

---

### Post by ronparent on 2010-08-23
Good move. I have kept the windows swap on a separate partition for some time. Now to keep ti off of the ssd.

What are you using to try to partition the ext4 and from where?

---

### Post by Gralamin on 2010-08-23
> **ronparent said:**
> Good move. I have kept the windows swap on a separate partition for some time. Now to keep ti off of the ssd.

What are you using to try to partition the ext4 and from where?

gparted (Assuming gparted is still used) in the 10.04 installer. In windows, it seems it was able to create the partitions, but was unable to turn them into ext4, etc.

---

### Post by ronparent on 2010-08-23
Gparted is used by the 10.04 installer. You can create a partition with windows but you will have to use a linux partitioner to format the ext4 (as well as create a swap). Gparted will not work in a 10.04 live CD session unless you install kpartx (using synaptics) prior to either partitioning or running the install from that same session. Once the kpartx is in place the install should proceed normally.

---

### Post by Gralamin on 2010-08-23
Ah, kpartx is probably what I forgot. I'll give that a try, and let you know how it goes. Thanks for the help.

---

### Post by Gralamin on 2010-08-23
kpartx did not seem to help, I am still getting the same error.

Likewise, if I create the partition in windows, and then order Linux to format it to ext4, with kpartx installed, it still doesn't work.

(Failed to create a file system - the ext4 file system creation in partition #7 of Serial ATA RAID isw_cecafgaibc_Volume0 (raid5_la) failed )

Edit: Aha! I  made the partitions in Gparted, and then installed without formatting. Obvious in hindsight.

Edit2: Now I need to install GRUB somewhere.
Edit3: Making a new thread about my GRUB issues.

---

