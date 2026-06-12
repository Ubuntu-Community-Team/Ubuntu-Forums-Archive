---
title: "Ubuntu does not detect Windows"
date: 2015-09-12
forum: Installation &amp; Upgrades
---

### Post by tom205 on 2015-09-12
So the actual problem is that Ubuntu (I have tried 12.04 and 14.04 - I know there are newer versions but I have this issue for some time and now is when I am certain to solve it) does not detect any other operating systems, although I have Windows 7 and have worked with it for quite some time. When I click advanced settings to see the partitions, there is only one thing - 1000GB free space (which is my whole hard disk and is in reality not free).

It all started when I first got Ubuntu (it was version 12.04) and had problems with the WiFi. So, of course, I looked for solutions and finally found some. After typing some stuff I didn't really understand in the terminal something happened and it all went black screen (I do not exactly remember what was the issue, maybe something with the kernel version). Anyway I ended up uninstalling Ubuntu. And surely I tried installing it again and that's when I got this problem.

I seriously have no idea what to do, as I said it only shows 1000GB free space in advanced settings, does not detect the windows partitions or...anything. Any help will be much appreciated.

---

### Post by nknwn on 2015-09-12
Did you accidentally delete Windows when you installed Ubuntu?

Which partitions are reported by GParted?

---

### Post by tom205 on 2015-09-12
I did not accidentally delete anything. I have my Windows 7 and it is working completely fine.

The thing is I do not see any partitions, it only says 1000GB free space and that's it.

---

### Post by yancek on 2015-09-12
> 
Which partitions are reported by GParted? 		

You forgot to answer the second question asked above.  You will have the GParted partitioner on the Ubuntu install medium.  Open that and see if you see anything different than the installer and if so, post the image here.  Also, when you attempt to install Ubuntu, which Installation Type option do you choose?  Best to use the manual method, referred to as "Something Else" in Ubuntu.

---

### Post by ubfan1 on 2015-09-12
Also check that your Windows machine is not using something called "dynamic partitions" -- those would need to be converted to regular partitions.

---

### Post by tom205 on 2015-09-13
So...GParted reports exactly 931.51GiB unallocated.

At the installation it only shows:
This computer currently has no detected operating systems. What would you like to do? - Erase disk and install Ubuntu - Something else.
When I click on the "something else" option to manage the partitions it shows only one thing: free space, size 1000204MB.

---

### Post by Bucky Ball on 2015-09-13
Welcome. Boot into Windows and switch off hibernate and fast start (could be called something else like 'fastboot'). If you have this on it locks the drive and Ubuntu won't be able to access it. Gparted will report something like free space where your partition should be.

There's four ways to switch off hibernate in Win [here]("http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html#option1"). Option 4 looks easy. 

Boot to the BIOS and switch off secure boot. 14.04 LTS is a good place to start. Supported until 2019. Use 'Something Else' when partitioning. Safer. Goes without saying, but I'll say it: make sure to backup anything valuable before continuing with an install of Ubuntu. 

Let us know how it goes. :)

---

### Post by tom205 on 2015-09-13
I did switch off hibernate and fast boot. I did not find from where exactly to switch off secure boot though. I mean I did open the BIOS but just didn't find the thing. Maybe I still just have to do that for anything to happen, because otherwise it's the same as before - GParted showing the 931GiB unallocated space and in the 'something else' menu in the installation process the free space only.

---

### Post by oldfred on 2015-09-13
Post these:
sudo parted -l
sudo fdisk -l

---

### Post by tom205 on 2015-09-14
```

ubuntu@ubuntu:~$ sudo parted -l 
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table. 
However, it does not have a valid fake msdos partition table, as it should. 
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT 
partition tables.  Or perhaps you deleted the GPT table, and are now using an 
msdos partition table.  Is this a GPT partition table? 
Yes/No? yes 
Model: ATA TOSHIBA MQ01ABD1 (scsi) 
Disk /dev/sda: 1000GB 
Sector size (logical/physical): 512B/4096B 
Partition Table: gpt 
 
Number  Start  End  Size  File system  Name  Flags 
  
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 
has been opened read-only. 
Error: Can't have a partition outside the disk!

```

```

ubuntu@ubuntu:~$ sudo fdisk -l 
 
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted. 
 
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes 
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 4096 bytes 
I/O size (minimum/optimal): 4096 bytes / 4096 bytes 
Disk identifier: 0x4c30ee64 
 
   Device Boot      Start         End      Blocks   Id   System 
/dev/sda1   *        2048      206847      102400    7   HPFS/NTFS/exFAT 
/dev/sda2          206848   314779647   157286400    7   HPFS/NTFS/exFAT 
/dev/sda3       314779648   465612799    75416576    7   HPFS/NTFS/exFAT 
/dev/sda4       629454848  1953521663   662033408    f   W95 Ext'd (LBA) 
/dev/sda5       629456896  1953521663   662032384    7   HPFS/NTFS/exFAT 
 
Disk /dev/sdb: 8019 MB, 8019509248 bytes 
16 heads, 32 sectors/track, 30592 cylinders, total 15663104 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x00000000 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1              32    15663103     7831536    7  HPFS/NTFS/exFAT

```

---

### Post by yancek on 2015-09-14
I don't know why you do not see any partitions detected in the installer but the reason you get  the Erase Disk and install Ubuntu message is because there is no free or unallocated space on which to install it.  You would need to boot into windows and use the Disk Management Utility to shrink one of your partitions so that you have unallocated space.

---

### Post by oldfred on 2015-09-14
Was drive originally Windows 8 with UEFI and gpt partitioning?
But then you installed Windows in BIOS boot mode?

Windows does not correctly convert a gpt partitioned drive to MBR(msdos). It leaves the backup gpt partition table (one of the advantages of gpt).

So if now using MBR, you must also delete the backup gpt data. Otherwise Linux tools see both MBR & gpt and get confused and assume you want to erase drive & start over correctly.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda

---

### Post by tom205 on 2015-09-14
> **yancek said:**
> I don't know why you do not see any partitions detected in the installer but the reason you get  the Erase Disk and install Ubuntu message is because there is no free or unallocated space on which to install it.  You would need to boot into windows and use the Disk Management Utility to shrink one of your partitions so that you have unallocated space.

I have about 78GB of memory which is unallocated space, at least that's what windows disk management says. Anyway I have no free space.

> **oldfred said:**
> Was drive originally Windows 8 with UEFI and gpt partitioning?
But then you installed Windows in BIOS boot mode?

Windows does not correctly convert a gpt partitioned drive to MBR(msdos). It leaves the backup gpt partition table (one of the advantages of gpt).

So if now using MBR, you must also delete the backup gpt data. Otherwise Linux tools see both MBR & gpt and get confused and assume you want to erase drive & start over correctly.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda

I am going to be honest here. I do not really understand this kind of stuff so much, so I don't know what to tell you. I am going to look into what you are asking and see what happens.

---

### Post by yancek on 2015-09-14
You may have space inside your various windows partitions but that won't help because you can't install Linux on a windows filesystem and expect it to work.  There isn't enough space outside your partitions for Ubuntu.  It might be a UEFI issue and if you can get some info on that, some of the members here are pretty good with it.

---

