---
title: "&quot;Guided resize and use freed space&quot; option disappeared!"
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by dkim on 2008-06-16
I've been searching to make sure that this is a repost, but so far I haven't found anything.
Anyway, when trying to dual boot my PC with the "Guided resize and use freed space", I got an error with a bunch of numbers (which I mindlessly neglected to write down). I restarted my computer and tried again, but the partition screen no longer shows the "Guided resize and use freed space" option. Does anyone know why? If this can't be fixed, can someone walk me through using the manual option to achieve the same results as the "Guided resize and use freed space" option?

In addition, I had to install a program that would allow me to boot Ubuntu from the CD, because my computer wouldn't load it from the CD without this program. This program came from the Ubuntu CD - how do I remove this program?

Many thanks!

---

### Post by meindian523 on 2008-06-16
I don't know why the option disappeared,but I think you should check the CD for errors and if it turns out OK,I can guide you through manual partitioning.

---

### Post by dkim on 2008-06-18
Hi! Thanks for the quick reply!
I executed a checksum on the iso file, and there were no problems. It seems like there are some issues with partitioning the drive. If it helps, I'm operating on Microsoft Windows XP Media Center Edition 2005. Could you give me steps on partitioning using the manual option to get the same results as using the guided resize option?
Thanks so much!

---

### Post by meindian523 on 2008-06-19
Well,what Windows OS doesn't affect how you partition your hard drive.Once you boot into the Live CD,could you post the results of typing the following in terminal:

```
sudo fdisk -l
```

---

### Post by dkim on 2008-06-20
The results of the execution are posted below
```

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8       29787   239207850    7  HPFS/NTFS
/dev/sda3           29788       30393     4867695   db  CP/M / CTOS / ...

```

Today I found that the guided partition option had strangely reappeared. However, after trying it again, I received the same error. That error went something along the lines of "error creating partition, process aborted" with no error code or anything else more specific.

Also, I was planning to make a 10 gb partition.

---

### Post by meindian523 on 2008-06-22
The CP/M / CTOS/ partition is used to recover your OS.Do you want Windows on your computer?If not,then you can delete that partition,let the Dell utility partition remain,because I don't know whether the utilities are generic or OS specific.Guided resize deletes all partitions on the HDD which you tell it to delete and creates partitions for Ubuntu.If you don't want Windows,do the following:

1]Go to System>>Administration>>Partition Editor
2]Delete your 2nd partition which is HPFS/NTFS which contains Windows.
3]Select the now uunallocated space and create an extended partition taking up the entire space.
4]Now select the unallocated space inside the extended partition you created and right click and select New.In file system,select ext3,and size of approximately 15-20 GB.
5]Select the remaining unallocated space,right click,click New.In filesystem,select linux-swap and size (2*size of your RAM).This is optional if you have RAM more than 2GB.
6]Select the remaining allocated space,right click,click New.In filesystem,select ext3,and size to how much ever is left of the unallocated space.
7]Start the installer,go to manual partitioning,select the 15-20 GB partition,select Edit partition,and use mount point as /
8]Select the biggest ext3 partition,created in step 6,click Edit partition and put in the mountpoint as /home.You don't need to format any of the partitions as you have already created them with the appropriate filesystems.Click Forward and go ahead with your install.

Enjoy!

---

### Post by dkim on 2008-06-25
I was actually hoping to keep the Windows partition - dedicating most of it to Windows, in fact. I wanted to create a 10 gb partition for Ubuntu just for casual internet browsing and text editing. Could you provide me instructions on creating a simple 10 gb partition for Ubuntu?
Thanks!

---

### Post by louieb on 2008-06-25
The live CD come with GParted @ System>Administration>Partition editor. 


[LIST]
[*]Shrink one of your partitions by 10GB
[*]Create an extended partition using the now unallocated 10GB
[*]Create a 9 - 9.5GB logical partition inside the extended partition
[*]use the remaining 1/2-1GB and create a swap partition.
[*]when installing use the manual option edit the new 9GB partition and mount it as / (root).
[/LIST]
Everything you need to know about GParted with illustrations [GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")

---

### Post by meindian523 on 2008-06-26
louieb is correct,provided you don't have Windows Vista.For Windows Vista,it's best to use Vista's own partitioner to do anything to Vista's partitions.Also,backup the stuff on your Windows partition to an external storage and defrag a few times before doing anything to the partitions.Once you delete a partition,it's data is (effectively)lost forever.
Effectively because you CAN use dd to recover it if nothing has overwritten your data since you deleted it's partition.

---

### Post by dkim on 2008-07-09
Thanks for all this information. Sadly, another issue arises. I followed the directions as stated. One point of confusion: when asking for the format of the 9.5 GB partition, I simply set it to ntfs, the same as my Windows partition. Is this a bad idea? How do I determine which file system I should be setting it to?
Anyway, I went ahead and tried it. It returned an error and stopped mid-process. I believe no partitions were actually written at the end. The detailed error file is shown below. Any help would be greatly appreciated.

```
GParted 0.3.5

Libparted 1.7.1

Shrink /dev/sda2 from 228.13 GiB to 218.36 GiB  00:29    ( ERROR )
     	
calibrate /dev/sda2  00:00    ( SUCCES )
     	
path: /dev/sda2
start: 112455
end: 478528154
size: 478415700 (228.13 GiB)
calculate new size and position of /dev/sda2  00:00    ( SUCCES )
     	
requested start: 112455
requested end: 458045279
requested size: 457932825 (218.36 GiB)
new start: 112455
new end: 458045279
new size: 457932825 (218.36 GiB)
check filesystem on /dev/sda2 for errors and (if possible) fix them  00:09    ( SUCCES )
     	
ntfsresize -P -i -f -v /dev/sda2
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 244948836864 bytes (244949 MB)
Current device size: 244948838400 bytes (244949 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 174199 MB (71.1%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 243903 MB 0
Multi-Record : 244201 MB 214863
$MFTMirr : 16780 MB 1
Compressed : 244184 MB 46919
Ordinary : 244949 MB 232390
You might resize at 174198525952 bytes or 174199 MB (freeing 70750 MB).
Please make a test run using both the -n and -s options before real resizing!
shrink filesystem  00:10    ( ERROR )
     	
run simulation  00:10    ( ERROR )
     	
ntfsresize -P --force --force /dev/sda2 -s 234461606399 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 244948836864 bytes (244949 MB)
Current device size: 244948838400 bytes (244949 MB)
New volume size : 234461602304 bytes (234462 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 174199 MB (71.1%)
Collecting resizing constraints ...
Needed relocations : 1380853 (5656 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
ERROR: Extended record needed (1040 > 1024), not yet supported!
Please try to free less space.
check filesystem on /dev/sda2 for errors and (if possible) fix them  00:10    ( SUCCES )
     	
ntfsresize -P -i -f -v /dev/sda2
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 244948836864 bytes (244949 MB)
Current device size: 244948838400 bytes (244949 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 174199 MB (71.1%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 243903 MB 0
Multi-Record : 244201 MB 214863
$MFTMirr : 16780 MB 1
Compressed : 244184 MB 46919
Ordinary : 244949 MB 232390
You might resize at 174198525952 bytes or 174199 MB (freeing 70750 MB).
Please make a test run using both the -n and -s options before real resizing!
grow filesystem to fill the partition  00:00    ( SUCCES )
     	
run simulation  00:00    ( SUCCES )
     	
ntfsresize -P --force --force /dev/sda2 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 244948836864 bytes (244949 MB)
Current device size: 244948838400 bytes (244949 MB)
New volume size : 244948832768 bytes (244949 MB)
Nothing to do: NTFS volume size is already OK.
real resize  00:00    ( SUCCES )
     	
ntfsresize -P --force --force /dev/sda2
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 244948836864 bytes (244949 MB)
Current device size: 244948838400 bytes (244949 MB)
New volume size : 244948832768 bytes (244949 MB)
Nothing to do: NTFS volume size is already OK.

========================================

Create Extended Partition #1 (extended, 9.77 GiB) on /dev/sda

========================================

Create Logical Partition #2 (ntfs, 9.28 GiB) on /dev/sda

========================================

Create Logical Partition #3 (linux-swap, 502.03 MiB) on /dev/sda

========================================
```

Thanks!

---

### Post by stchman on 2008-07-09
> **dkim said:**
> I've been searching to make sure that this is a repost, but so far I haven't found anything.
Anyway, when trying to dual boot my PC with the "Guided resize and use freed space", I got an error with a bunch of numbers (which I mindlessly neglected to write down). I restarted my computer and tried again, but the partition screen no longer shows the "Guided resize and use freed space" option. Does anyone know why? If this can't be fixed, can someone walk me through using the manual option to achieve the same results as the "Guided resize and use freed space" option?

In addition, I had to install a program that would allow me to boot Ubuntu from the CD, because my computer wouldn't load it from the CD without this program. This program came from the Ubuntu CD - how do I remove this program?

Many thanks!

Dumb question, but do you have ANY free space on the hdd you want to install?

Free and unallocated is the same.  Launch gparted and see if you see and grey in hdd partitions.

---

### Post by dkim on 2008-07-24
I sure do. I guess Ubuntu just hates my computer.

---

