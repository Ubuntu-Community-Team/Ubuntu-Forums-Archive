---
title: "Installing Ubuntu with Windows 7"
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by melwaltrip on 2009-12-25
I am a novice at partitioning and a beginner with Ubuntu.

Need help installing Ubuntu 9.10 alongside Windows 7:

I get down to Step 4 of 6 on the Install menu -

It shows that my hard drive has 3 sections:
/dev/sda1 Used by Toshiba
/dev/sda2 Windows 7 (Loader) 
/dev/sda3 which is empty and that is where I want to put Ubuntu

It asks if I want to format the drive and use it all for Ububtu or if I want to partition manually...since I want both operating systems I select "partition manually"

On Step 4 of 7 I select /dev/sda3 since that is where I want to put ubuntu

I get an error message that says" No root file system is defined. Please correct this from the partitioning menu"   

At this point I am lost....How do I get Ubuntu installed i /dev/sda3??

---

### Post by raymondh on 2009-12-25
> **melwaltrip said:**
> I am a novice at partitioning and a beginner with Ubuntu.

Need help installing Ubuntu 9.10 alongside Windows 7:

I get down to Step 4 of 6 on the Install menu -

It shows that my hard drive has 3 sections:
/dev/sda1 Used by Toshiba
/dev/sda2 Windows 7 (Loader) 
/dev/sda3 which is empty and that is where I want to put Ubuntu

It asks if I want to format the drive and use it all for Ububtu or if I want to partition manually...since I want both operating systems I select "partition manually"

On Step 4 of 7 I select /dev/sda3 since that is where I want to put ubuntu

I get an error message that says" No root file system is defined. Please correct this from the partitioning menu"   

At this point I am lost....How do I get Ubuntu installed i /dev/sda3??

Hi,

Unless I am mistaken, a standard win7 set-up coming from a manufacturer will have 3 partitions.... RECOVERY + BOOT IMAGE + WIN7.

If above is correct and from reading your post, you may overwrite your win7 OS.  So be careful!

If you need help/assistance in verifying, I will need you to either copy/paste a visual of windows' disk management utility output or.... boot into the liveCD and go live session (try ubuntu).  Once you have the live session desktop, access a terminal (applications > accessories) and type

```
sudo fdisk -l
```

small L.  Paste that result in your next post.

A quick guide using the automated process in the ubuntu installer:

1.  back-up your files
2.  Defrag windows 2x first.
3.  Using the same disk management utility, use that to shrink windows to give space for Ubuntu. How much space is your preference but try to give Ubuntu at least 15-20gb (noting that it won't hold much media files later on).  Leave that space unallocated/free/unpartitioned
4.  Exit the utility and reboot windows.  Let windows run its' disc integrity check and make sure win7 boots fine.
5.  Once OK, exit/close windows and boot into the Ubuntu liveCD
6.  In step 4 of the install process, make sure the unallocated space is identified properly.  If not, we can try the manual method so do post back if you have the issue.
7.  If OK, select to install in 'largest continuous free space'.  Again, the size ought to be similar to the size you prepared some steps ago.
8.  Continue with the install.

Post back if you are unsure or the installer does not give you the 'largest continuous' option.  We can/will create the ubuntu partitions beforehand and do a manual install.

Just to be clear, a manual install will require you to
- select the partition (which should not be win7's)
- mount a root filesystem which will be a slash (/)
- Format root partition to either ext3 or ext4 (default is ext4) which will OVERWRITE ANY EXISTING DATA on that partition.
- select and mount a linux SWAP file system.


Regards,

---

### Post by melwaltrip on 2009-12-25
Thanks Raymond....not sure I understand all of it but will take it one step at a time and see how far I get....

---

### Post by raymondh on 2009-12-25
> **melwaltrip said:**
> not sure I understand all of it but will take it one step at a time ...

Better safe 'eh ;)

step 1.

Back-up your files

Step 2

Let's verify what your HD currently contains.  Boot into the Ubuntu liveCD and select "TRY UBUNTU WITHOUT ANY CHANGES" (known as live session).  Once in live session, access a terminal (from applications > accessories).... type and post back the results of

```
sudo fdisk -l
```

I know you copied the installer output in your first post.  I just want to verify that sda3 is indeed UNALLOCATED (if it is, it would not be listed as sda3)  I am being cautious because I know a default win7 install makes 2 partitions (a boot image about 100mb and, the C: drive) and the manufacturer adds a recovery partition.


As mentioned earlier, if I am wrong, then go ahead and install in sda3.  But if I am right and you do install, your next post will/might be ... "I lost my win7 install" :)

Regards,

---

### Post by Mark Phelps on 2009-12-25
If you did not manually create the partition being referred to as "sda3", then it really is your Win7 OS partition -- and doing anything to it with the Ubuntu installer is running the risk of corrupting it!

Best course of action is to use the Win7 Disk Management utility to shrink the Win7 partition (NOT the one indicated as System Reserved!) to make room for Ubuntu.  Don't create a partition in the unallocated free space, just leave it alone.

When you boot from the Ubuntu CD, it's installer should then give you the option of installing inside the unallocated space.

---

### Post by melwaltrip on 2009-12-25
This is what I get when I do the sudo fdisk -l command:




ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5f6282a5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        9141    71888058+   7  HPFS/NTFS
/dev/sda3            9142       14594    43795741    7  HPFS/NTFS
ubuntu@ubuntu:~$

---

### Post by raymondh on 2009-12-25
> **melwaltrip said:**
> This is what I get when I do the sudo fdisk -l command:




ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5f6282a5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        9141    71888058+   7  HPFS/NTFS
/dev/sda3            9142       14594    43795741    7  HPFS/NTFS
ubuntu@ubuntu:~$

-Boot into windows and access the disk management utility.  Use that to defrag (2x if you have the time) and then.... shrink sda3 to give space for ubuntu. Leave that ubuntu-space unallocated (not partitioned).  Exit and reboot windows.  Let it do its' check disk and then make sure it loads fine.

-Boot into the liveCD and install. IN step 4, choose "largest continuous free space".

Let's not mess with any win7 (whether C or D drives) and recovery
partitions.

Do you have a working/tested back-up of your files.  Do so before working on any partitions.

---

### Post by melwaltrip on 2009-12-25
You mates were right on the money. I followed your instructions and am now a happy camper with Windows AND Ubuntu operating systems working. Thanks very much, you probably saved me from losing Windows in the process.

---

### Post by raymondh on 2009-12-25
> **melwaltrip said:**
> You mates were right on the money. I followed your instructions and am now a happy camper with Windows AND Ubuntu operating systems working. Thanks very much, you probably saved me from losing Windows in the process.

You're welcome.  Glad you have it going without posting a new thread "I lost my windows" :)

Happy holidays and ubuntu-ing.

PS.  You can mark this thread solved using thread tools.

---

