---
title: "How to Manual Partition - Fresh reinstall of Intrepid 64 Bit replacind Hardy 32 Bit"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by keech on 2008-11-09
Hi Friends,

I have presently have Ubuntu 8.04 32 Bit on my PC. It's a hard disk formated as per attached screen shot. I wish to upgrade to Ubuntu 8.10 64 Bit. I want to do a fresh install. I have taken all my media, documents to a different partition. Can I install the new one on the same partition, if so how? I want this without disturbing the other partition.

Kindly help me please.

Thanks in Advance

---

### Post by bulldog on 2008-11-09
Yes you can install on the same partition.

However,I want to suggest something.
I saw on the screenshot you use a 34GB partition for both,/ and /home.
Maybe you can consider to make an extra partition about 8-10GB for the /
and the remaining 24GB for a separate /home partition.
This has some advantage in the future when you want to reinstall or do a fresh install,you can keep all your data on the /home partition and re-mount it on the new install WITHOUT formatting.

But back to your question,yes you can,choose manual when you come to the partitioner and mount the correct partition as / and set it to format ext3,and set the bootflag on

---

### Post by keech on 2008-11-09
> **bulldog said:**
> Yes you can install on the same partition.

However,I want to suggest something.
I saw on the screenshot you use a 34GB partition for both,/ and /home.
Maybe you can consider to make an extra partition about 8-10GB for the /
and the remaining 24GB for a separate /home partition.
This has some advantage in the future when you want to reinstall or do a fresh install,you can keep all your data on the /home partition and re-mount it on the new install WITHOUT formatting.

But back to your question,yes you can,choose manual when you come to the partitioner and mount the correct partition as / and set it to format ext3,and set the bootflag on
Thank bulldog, I am novice so I dont want to try this as I may not know what to do but want to know the following
1.) Should I format sda1 or sda5 and sda6 separately?
2.) If I have to format sda1, then should I create sda5 and sda6 manualy?

Thanks in Advance

---

### Post by bulldog on 2008-11-09
You can't format an extended partition,it's only there to hold your logical partitions.
Can't figure out why there's boot written by the extended partition though.

When you're gonna install ubuntu,you will meet the partitioner.
Now you have to choose for manual.
You get an oversight of the existing partitions.
Choose the one [sda5] set it to format ext3,mountpoint / and set bootflag on.
Then choose the swap partition,which in most cases will be mounted as swap without any interfering from you,but take a look to be certain.

Write changes to disk and proceed with the install.
No need to do anything with the other partitions.

To be on the safe side,can you give me the output from ```
sudo fdisk -lu
```in a terminal?

---

### Post by keech on 2008-11-09
> **bulldog said:**
> You can't format an extended partition,it's only there to hold your logical partitions.
Can't figure out why there's boot written by the extended partition though.

When you're gonna install ubuntu,you will meet the partitioner.
Now you have to choose for manual.
You get an oversight of the existing partitions.
Choose the one [sda5] set it to format ext3,mountpoint / and set bootflag on.
Then choose the swap partition,which in most cases will be mounted as swap without any interfering from you,but take a look to be certain.

Write changes to disk and proceed with the install.
No need to do anything with the other partitions.

To be on the safe side,can you give me the output from ```
sudo fdisk -lu
```in a terminal?
Bulldog, this is the output


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000a8f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   147701610   222082559    37190475    5  Extended
/dev/sda3              63    73850804    36925371    7  HPFS/NTFS
/dev/sda4       222082560   312576704    45247072+   7  HPFS/NTFS
/dev/sda5       147701673   218933819    35616073+  83  Linux
/dev/sda6       218933883   222082559     1574338+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by bulldog on 2008-11-09
Okay,it should be done as I stated before.
sda1 is the extended partition and sda5 is the partition to install / ,and sda6 is the swap partition.

Just mount the correct partitions to / and swap and you're good to go.:D

---

### Post by keech on 2008-11-09
> **bulldog said:**
> Okay,it should be done as I stated before.
sda1 is the extended partition and sda5 is the partition to install / ,and sda6 is the swap partition.

Just mount the correct partitions to / and swap and you're good to go.:D
Thanks Bulldog, I still have a doubt, why I am seeing boot flagon for sda1 now and if I enable sda5 boot flag on will it not have conflict or change the setting, apologies if this is a silly question.

---

### Post by bulldog on 2008-11-09
Yes,I mentioned that one in an earlier post.
I don't know how you managed to get the bootflag on an extended partition.
That's why I asked for the sudo fdisk command,to be sure it is an extended partition.

In my opinion you can simple install as I stated before,and don't worry about the bootflag in the extended partition.
It will be placed on the sda5 partition and removed from the extended partition.

---

### Post by keech on 2008-11-10
> **bulldog said:**
> Yes,I mentioned that one in an earlier post.
I don't know how you managed to get the bootflag on an extended partition.
That's why I asked for the sudo fdisk command,to be sure it is an extended partition.

In my opinion you can simple install as I stated before,and don't worry about the bootflag in the extended partition.
It will be placed on the sda5 partition and removed from the extended partition.
Hi,

When I press forward it gives me the attached error msg kindly help

Thanks in Advance

---

### Post by bulldog on 2008-11-10
You have to mount sda5 to / NOT to /boot
Just / that is the file system.
If you want a separate /boot,you'll have to create an extra partition.

Summary:
sda5 set to format ext3,next mountpoint is /,next,bootfag is on, DONE
sda6 set it to format as swap,next,mountpoint is swap,nothing more to do.
Write changes to disk,and proceed.

---

### Post by keech on 2008-11-13
> **bulldog said:**
> You have to mount sda5 to / NOT to /boot
Just / that is the file system.
If you want a separate /boot,you'll have to create an extra partition.

Summary:
sda5 set to format ext3,next mountpoint is /,next,bootfag is on, DONE
sda6 set it to format as swap,next,mountpoint is swap,nothing more to do.
Write changes to disk,and proceed.
Hi Bulldog,

I have installed it successfully, no issues but on the whole I think 32 Bit works smoother than 64 Bit, as of today.

Thanks for all your help

---

