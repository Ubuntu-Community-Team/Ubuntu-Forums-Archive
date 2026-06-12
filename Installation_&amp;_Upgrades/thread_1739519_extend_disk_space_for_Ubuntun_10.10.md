---
title: "extend disk space for Ubuntun 10.10"
date: 2011-04-26
forum: Installation &amp; Upgrades
---

### Post by alwaysonnet on 2011-04-26
Hello all,

I've 80G hard-disk with dual boot ( XP with 5.5G and Ubuntu 10.10 with 4.5G ). After recent updates there is only 1G of space left on Ubuntu.

I've 3 more drives with around 25G left and want to extend Ubuntu by another 10G.

How can I do that? 

Many Thanks in advance.

---

### Post by dino99 on 2011-04-26
your installation need to looks like:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by alwaysonnet on 2011-04-26
I've already installed both OS and want to extend my Ubuntu partition to another 10G.

@dino99:
Sorry If I've misunderstood your reply earlier.

---

### Post by Hedgehog1 on 2011-04-26
Here is a thread of mine with some pictures that show how we combine multiple drives in Linux to make a larger filesystem:

[**How Linux makes larger 'file systems' using /etc/fstab**]("http://ubuntuforums.org/showthread.php?t=1705788")

The second picture is what **dino99** was explaining.

The last picture may be a good fit for your situation, too.

Also, Drives are cheap now-a-days.  That is another option for more storage and better disk performance, too.


***The Hedge***

:KS

---

### Post by SecretCode on 2011-04-26
> **alwaysonnet said:**
> 
How can I do that? 


By repartitioning your drive ... I assume you knew that. How are they currently partitioned? Post output of 
```
sudo parted -l
```
and
```
df -hT
```

(While I agree with The Hedge about combining partitions, your main Ubuntu partition is very small and I do think you should increase it.)

---

### Post by alwaysonnet on 2011-04-26
@SecretCode:

Here is the output from my terminal....

```

Model: ATA ST340015A (scsi)
Disk /dev/sda: 40.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      2048B   5825MB  5825MB  primary   fat32           boot, lba
 2      5826MB  40.0GB  34.2GB  extended                  lba
 8      5826MB  10.5GB  4640MB  logical   ext4
 9      10.5GB  10.7GB  271MB   logical   linux-swap(v1)
 5      10.7GB  16.0GB  5243MB  logical   fat32           lba
10      16.0GB  21.5GB  5486MB  logical   fat32
 6      21.5GB  32.2GB  10.7GB  logical   fat32           lba
 7      32.2GB  40.0GB  7807MB  logical   fat32           lba


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                                  

tanmayee@sistas:~$ df -hT
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda8     ext4    4.3G  3.1G 1018M  76% /
none      devtmpfs    740M  256K  740M   1% /dev
none         tmpfs    746M  556K  745M   1% /dev/shm
none         tmpfs    746M   92K  746M   1% /var/run
none         tmpfs    746M     0  746M   0% /var/lock
/dev/sr0   iso9660    658M  658M     0 100% /media/Varun (Songs)


```

---

### Post by SecretCode on 2011-04-26
OK. I assume XP is on the first partition. (Odd that it's fat32 rather than ntfs, though.)

What is on each of the other 4 partitions? (If they have useful data why don't you mount them in Ubuntu? And do you still want that many separate partitions?)

Can you move data around? The easiest approach will be to move all the data off partition 5 (size 5243MB) - and then, in GParted running on a live CD, **delete** partition 5 and partition 9 (the swap), then **extend** partition 8 (Ubuntu) and make a new swap partition. 

Have you backed up everything? :) Partition editing can mess up your whole drive.

---

### Post by alwaysonnet on 2011-04-27
@SecretCode

I don't have any data residing on partitions numbered 5, 6, 7, 10. They're clean now.

I've installed GParted from 'Ubuntu Software Center'. Is that fine or Do I need to download to make a 'Live CD'.

---

### Post by DanceLink on 2011-04-27
I'm inclined to ask why you have a 10 GB partition with nothing on it, let alone that many partitions on your hard drive.

You should be able to delete partitions 5,6,7,10 through GParted, but in terms of extending Ubuntu, you may need a LiveCD. Not sure though, but GParted helps, and is a VERY handy tool to have around.

---

### Post by SecretCode on 2011-04-27
> **alwaysonnet said:**
> I've installed GParted from 'Ubuntu Software Center'. Is that fine or Do I need to download to make a 'Live CD'.

You **must** run GParted from a Live CD - it can't change the partitions if you have any of them mounted. A regular (not "alternative") Ubuntu installation CD is perfect - GParted is included.

> **alwaysonnet said:**
> I don't have any data residing on partitions numbered 5, 6, 7, 10. They're clean now.

This is going to be easy then! But it does beg the question - what partitions do you actually want? You have a free hand and can get the right partition layout now (we just won't touch partition 1 (XP) or resize the extended partition 2). 

I assumed they were for documents, music etc. (Or for other operating systems.) Why so many?

---

### Post by alwaysonnet on 2011-04-27
@SecretCode ~

> I assumed they were for documents, music etc. (Or for other operating systems.) Why so many?

You're right. I kept them for movies, music and other important stuff.

I really want partitions 5, 10 to extend them for Ubuntu now. Let me know how to proceed.

Many Thanks in advance.

---

### Post by Dutch70 on 2011-04-27
Open Gparted & take a screenshot of your partitions, that will make it a little easier. Attach them to your next post with the paper clip in the toolbar.

Also, how much physical RAM do you have? Your swap partition only needs to be equal to, or slightly larger than your RAM. 

FAT32 is not necessary, you should use ntfs if you want to share with windows. If not, just use ext4. On the other hand, you can use ext3 and share with windows if you install fs-driver. 

Also, as everyone is asking, why so many partitions? It's not sufficient with the disk space that you have. You can just use folders and basically accomplish the same thing and get the most usage out of your hdd.

---

### Post by DanceLink on 2011-04-27
> **Dutch70 said:**
> Also, how much physical RAM do you have? Your swap partition only needs to be equal to, or slightly larger than your RAM.

Odd, my laptop has 1.5 GB of RAM, yet my swap is 4 GB.  

> **Dutch70 said:**
> Also, as everyone is asking, why so many partitions? It's not sufficient with the disk space that you have. You can just use folders and basically accomplish the same thing and get the most usage out of your hdd.

Seconded.

---

### Post by SecretCode on 2011-04-27
Hold on, something is not right here. You said it was an 80GB drive, but the parted output says it's 40GB. Is it really 40GB?

Are you able to get a bigger internal drive? You probably can't buy drives smaller than 250GB now. And/or are you able to buy an external drive for all your data?

Assuming you want XP, Ubuntu and some shared data on this drive, I would recommend this partition layout:
- sda1 - XP - completely unchanged - 5825MB
- all the rest of the drive in an extended partition, sda2, which is also unchanged
- 3 logical partitions: 20GB for Ubuntu, 1GB for swap (more if you want), and the rest for data.

Your procedure would be this:
1. Back up everything not already backed up
2. Download and burn an Ubuntu Live CD. Doesn't matter what version.
3. Boot it and run GParted.
4. **Delete** partitions 9, 5, 10, 6 and 7 of your current layout, and apply those changes. This should be quick. You should end up with 2 partitions and 25-30GB of unallocated space.
5. **Resize** the first logical partition (it will probably be labelled sda8) to 20GB. Apply. This might take several minutes.
6. **Create** a new partition in the unallocated space of 1 or 2GB and format it as **swap**. **Create** another new partition using all the remaining unallocated space and format it as **ntfs** or **fat32** (either is OK). Apply these changes. Should take less than a minute, I think.

Then reboot into Ubuntu.

---

### Post by SecretCode on 2011-04-27
> **DanceLink said:**
> Odd, my laptop has 1.5 GB of RAM, yet my swap is 4 GB.  


You need slightly more swap than RAM if you want to use hibernation.

Otherwise ... you don't actually need any swap at all. Unless it's on a superfast dedicated physical drive, it's certain that if your machine starts using swap it will slow down dramatically.

For occasional use (because "slow" is better than apps refusing to open at all), any amount of swap helps. But I doubt you will use 4GB of swap on top of 1.5GB of RAM and be happy with it!

---

### Post by alwaysonnet on 2011-04-27
> **SecretCode said:**
> Hold on, something is not right here. You said it was an 80GB drive, but the parted output says it's 40GB. Is it really 40GB?

Are you able to get a bigger internal drive? You probably can't buy drives smaller than 250GB now. And/or are you able to buy an external drive for all your data?

Assuming you want XP, Ubuntu and some shared data on this drive, I would recommend this partition layout:
- sda1 - XP - completely unchanged - 5825MB
- all the rest of the drive in an extended partition, sda2, which is also unchanged
- 3 logical partitions: 20GB for Ubuntu, 1GB for swap (more if you want), and the rest for data.

Your procedure would be this:
1. Back up everything not already backed up
2. Download and burn an Ubuntu Live CD. Doesn't matter what version.
3. Boot it and run GParted.
4. **Delete** partitions 9, 5, 10, 6 and 7 of your current layout, and apply those changes. This should be quick. You should end up with 2 partitions and 25-30GB of unallocated space.
5. **Resize** the first logical partition (it will probably be labelled sda8) to 20GB. Apply. This might take several minutes.
6. **Create** a new partition in the unallocated space of 1 or 2GB and format it as **swap**. **Create** another new partition using all the remaining unallocated space and format it as **ntfs** or **fat32** (either is OK). Apply these changes. Should take less than a minute, I think.

Then reboot into Ubuntu.
@SecretCode:

It was my mistake. I do own a 40G hard-disk not 80G and 1.5G RAM

---

### Post by SecretCode on 2011-04-27
Even more reason not to have so many partitions, then!

Post a screenshot from GParted so we can be 100% clear.

---

### Post by alwaysonnet on 2011-04-27
Screen shot of my drive with GParted.

---

### Post by Dutch70 on 2011-04-27
Ok, here is my recommendation.

Solution 1
Delete sda5,6,7,9,10.
Grow sda8 to at least 8-10GB *(if you use more than 75% your system will slow down)*
Create a 3-3.5GB swap partition at the far right side of your hdd.
Create a data partition with the remainder of your hdd. Format it to NTFS not FAT.

Solution 2 *(requires reinstall)*
Delete all of your partitions 
Create a swap partition *(as mentioned above)*
Create a new / partition with all of your unallocated space and format to ext3. *(install here)*


Install fs-driver into windows so that you can access your ext3 partition. 
[[COLOR="RoyalBlue"]http://sourceforge.net/projects/ext2fsd/[/COLOR]]("http://sourceforge.net/projects/ext2fsd/")

---

### Post by SecretCode on 2011-04-27
^ What he said, solution 1 in particular. Except I would make sda8 even bigger than 10GB.

---

