---
title: "Software RAID 5"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by ilias74 on 2010-05-16
Hi,
I have three 250GB disks on my server and I tried to create a RAID5 array during installation for abount 6-7 times on Ubuntu Server 10.04 64bit, always failing.
Maybe I miss something about the RAID basic concepts but I really need help.
Here is the partitions configuration I tried to use:

sda >> sda1 : software raid volume
           sda2 : /boot
           sda3 : swap

sdb >> sdb1 :  software raid volume

sdc >> sdc1 : software raid volume

md0 >> sda1+sdb1+sdc1

md0 mount point: /

Installation completes ok with no errors ad data is written on all 3 disks.

On reboot though I get errors about some paths related to /proc missing and a disk UUID not found. System falls back to initramfs.

I also tried to put /boot on a raid1 array by creating a boot partition on sdb too (sda2+sdb2) with no results.

I apologise if I miss something far too elementary.

---

### Post by darkod on 2010-05-16
Not sure if it's an issue, but for better performance have you tried making symmetric partitions on the drives? You don't have to use them, just to make the drives look the same.

sda1 /boot
sda2 for raid
sda3 swap

sdb1 unused, same size as sda1
sdb2 for raid
sdb3 swap

etc

You don't even have to chain the swaps into raid, you can add more than one swap partition in ubuntu later and set same priority and that will use them as if they were in raid. On the other hand, since you want RAID5 and not only RAID0, you might as well raid the swaps too.

---

### Post by ilias74 on 2010-05-16
Thanks for your answer. Yes, I tried to use that scheme too. In that case, things went better, meaning that the array was created but the system did boot with a degraded array and reported something about sda, sda1 and sdb and sbd1 similarity which created the problem and suggested to use zero superblock command for the sda and sdb devices. I did so but the system could not boot after that.
I am tempted to use another disk, on which install the OS and use the other 3 as RAID5. I could create the array with mdadm from within the OS in that way. But I would prefer not to use another disk. What I don't remember is if, in the schema you suggested,  I had put /boot on sda1 or not.
Oh, and maybe I should mention I disabled sata-raid in BIOS, so it's not the case of some interference.
Is the scheme you reported the one you'd use? What is the optimal partition/raid scheme you suggest for a RAID5 with 3 disks available for OS and data?
Thanks again!

---

### Post by darkod on 2010-05-16
I don't have 3 disks and I'm not too experienced in raid, but I have been reading about it and planning it, maybe. :)

First, for software raid /boot absolutely has to be OUTSIDE the array, at least to my knowledge. So if you don't remember whether you had /boot outside the array when you tried to do the above scheme, it's worth trying again.

Second, in this situation, speaking about the actual raid array, I would create one single raid5 device from the three partitions. Then I would use that raid5 device as physical volume for LVM.

In that case you don't have to worry and plan the partitioning too much. LVM allows you to resize partitions later, live and without formatting them again. You can start with smaller partitions for /, /home, etc, and enlarge them as needed. You can do that as much as you want until you hit the size of the raid5 device which is of course your limit.

Some reading material on LVM, this is for setting up on 8.10 but it's the same. Also, it doesn't matter if the physical device used for LVM is single disk, or raid device.
[http://linuxbsdos.com/2008/11/11/lvm-configuration-in-ubuntu-810/all/1/](http://linuxbsdos.com/2008/11/11/lvm-configuration-in-ubuntu-810/all/1/)

There are tons of articles about LVM in google too.
I have this bookmarked for software raid also:
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

---

### Post by mistichu on 2010-05-16
i dont mean to be rude an hijack your thread but could someone explain Software raid ?? i dont understand how thats possible ? is it just like several partitions on one drive ? or just several drives setup on an older system without raid capabilities?

---

### Post by ilias74 on 2010-05-16
Thanks darkod, I believe LVM is a great solution. I will seriously take it into consideration for my md arrays. But I still hope the raid configuration issue is not an OS related one. I would't like to go back to SuSE... (I have more than 5 happy raid1 systems running on it).

As about mistichu: I am far from being an expert on raid implementations. But for as far as I know software RAID performance is the same as some hardware RAID solutions. 
I confirm you can do it with some old hardware with simple ATA IDE disks on it. 
Software RAID follows the same rules as hardware RAID does. 
What changes is the channel through which the syncing is done. Obviously an older system will have performance issues. That depends on raid level too. E.g. a raid1 write performance equals that of the slowest drive, but nearly doubles the read time.
It is not only about partitioning a single hdd, but creating multidisk devices. The arrays of disks have different kinds of specifications. 
You can find info about raid levels here:
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

---

### Post by darkod on 2010-05-16
> **mistichu said:**
> i dont mean to be rude an hijack your thread but could someone explain Software raid ?? i dont understand how thats possible ? is it just like several partitions on one drive ? or just several drives setup on an older system without raid capabilities?

In short, the raid function in motherboard BIOS common these days is also in a way software raid even though you might think the mobo hardware is doing the work. That's why it's usually called fakeraid.

The ubuntu software raid is a function of the OS (it is also included in the desktop version, not just server) where it takes a number of partitions depending of the raid type, and creates a raid array from them. However, they can't be partitions on the same disk. You need at least 2 disks for raid, in case of raid5 the minimum is 3 for example.

People have reported better performance of the software raid compared to the fakeraid. So even if your mobo supports fakeraid, it seems software raid is better option. Usually you would use fakeraid if you want to dual boot with windows because the software raid function is present in ubuntu and windows could not be on that array.

If the computer has no raid capability, you could still use software raid.

---

### Post by mistichu on 2010-05-16
thanks for the info guys

---

### Post by ratcheer on 2010-05-16
My personal opinion after working with RAID on enterprise-class servers for many years is, if you dont have at least five identical drives for a RAID-5 array. do something else.

Tim

---

### Post by ilias74 on 2010-05-16
Well,  I work for SOHO and SB environments (5-30 users) at the moment, but could you explain why the 3 disk array would be unsuitable? And I would be glad if you could give me some help with the installation problem I have with raid5 on those 3 disks using the ubuntu 10.04 installer to partition and make raid devices. I don't think I have to give up on RAID5 just because I have 3 disks instead of 5, it doesn't make sense to me.
Thanks.

---

### Post by ratcheer on 2010-05-16
Its hard for me to remember everything because I gave up on RAID-5 in 1996 due to poor performance. Since 1999, I have stuck with RAID 1+0 (aka RAID 10). 

But, with a 3-drive RAID-5 array, one of the drives is used for parity. If you lose a single drive, you have to recover 1/2 of your data when you are reestablishing the array. IMHO, there is just not enough of an advantage to be an advantage.

Whatever floats your boat....

Tim

---

### Post by ilias74 on 2010-05-17
Ok, thanks for the answer. Your opinion is more clear now. But can you tell me if the procedure for creating my raid5 is right? You can read about it on my thread starting message.
Anyway, I should try again thursday and I hope I won't waste time again...

---

### Post by ratcheer on 2010-05-17
I wish I could be more help, but I have never done RAID on Linux systems. I have always done it on big Sun UNIX machines with plenty of hardware (multiple RAID controllers with multipathing support to the disks) and software (e.g., Veritas Volume Manager, a high-end LVM). I am probably more lost on the small systems than you.

It sounds like you are setting up hardware RAID, though. Is that correct? If yes, wouldn't the LUN just be presented to the software (Linux) as a disk address that you would then create filesystems on, presumably with something like Gparted?

Don't let my confusion confuse you. I need to get out of this conversation.

Tim

---

### Post by ilias74 on 2010-05-17
Don't worry! All answers and opinions are welcome.
Well, it's software RAID, not a hardware one. I created software RAID1 arrays on many systems till now without issues. It's RAID5 giving me a headache on ubuntu. But I'll have news on thursday, when I'll try again. Thanks anyway :)

---

### Post by Saghaulor on 2010-05-17
I'm having a similar issue.

Trying to setup software raid on three physical drives.

raid1 for /boot
raid10 for /
raid1 for swap

The install seems to go as planned, and then the reboot goes to busy box.

I've tried installing /boot on a regular physical partition, and that doesn't seem to help either. the system would boot into grub rescue mode.

I found this post on resolving the issue, but I didn't have much luck. [https://help.ubuntu.com/community/Grub2#Grub shows rescue prompt (and does not continue to boot)]("https://help.ubuntu.com/community/Grub2#Grub shows rescue prompt (and does not continue to boot)")

Any help would be appreciated.

---

### Post by Saghaulor on 2010-05-19
bump

---

### Post by ilias74 on 2010-05-19
hi,
I tested raid5 with symmetric partitions on 3 virtual disks on vmware. Ubuntu server 10.04 32 bit, all went fine. I may have an issue with real disks on my physical machine or some problem with the 64 bit edition? I will be able to tell you tomorrow...

---

### Post by ilias74 on 2010-05-21
Hi!
I confirm that this might be a 64 bit version issue in my case. It went absolutely ok on vmware ubuntu 32-bit server edition, and yesterday I put SuSE 11.2 64-bit edition on the physical server and sw raid5 worked right away on first install with no issues.

---

### Post by Saghaulor on 2010-06-02
> **ilias74 said:**
> Hi!
I confirm that this might be a 64 bit version issue in my case. It went absolutely ok on vmware ubuntu 32-bit server edition, and yesterday I put SuSE 11.2 64-bit edition on the physical server and sw raid5 worked right away on first install with no issues.

It's not a 64bit issue, because I was trying to install 32bit server. 

I'm pretty sure it's a Ubuntu 10.04 issue. I was successful in installing The setup with a previous version, 9.10, I think it was.

---

### Post by wkulecz on 2010-06-02
> My personal opinion after working with RAID on enterprise-class servers for many years is, if you dont have at least five identical drives for a RAID-5 array. do something else.


My personal experience at home with software (MDADM) raid-5 using three drives is don't, at least with XFS filesystems.  Lost all data when one of the drives failed to start after a reboot because of a loose power connector.

Fortunately I run an rsync cron job to backup the raid to a single large drive nightly, so I was back up quickly, but always remember, raid is not backup!

My advice to the home user would be to forget about MDADM raid or fakeraid and get a second drive for backups instead.  I do consider fakeraid (RAID-1) essential for Windows due to the difficulty of backing it up such that you do not need to reinstall it and all your applications, but buy a separate drive for Linux if you want to multi-boot.

---

### Post by Saghaulor on 2010-06-03
> **wkulecz said:**
> My personal experience at home with software (MDADM) raid-5 using three drives is don't, at least with XFS filesystems.  Lost all data when one of the drives failed to start after a reboot because of a loose power connector.

Fortunately I run an rsync cron job to backup the raid to a single large drive nightly, so I was back up quickly, but always remember, raid is not backup!

My advice to the home user would be to forget about MDADM raid or fakeraid and get a second drive for backups instead.  I do consider fakeraid (RAID-1) essential for Windows due to the difficulty of backing it up such that you do not need to reinstall it and all your applications, but buy a separate drive for Linux if you want to multi-boot.

Yeah, I was trying to build a test server, that will host a ruby on rails app plugged into postgresql, so I wanted the redundancy not just for data integrity, but also for performance.

---

### Post by de0xyrib0se on 2010-10-14
> **ratcheer said:**
> Its hard for me to remember everything because I gave up on RAID-5 in 1996 due to poor performance. Since 1999, I have stuck with RAID 1+0 (aka RAID 10). 

But, with a 3-drive RAID-5 array, one of the drives is used for parity. If you lose a single drive, you have to recover 1/2 of your data when you are reestablishing the array. IMHO, there is just not enough of an advantage to be an advantage.

Whatever floats your boat....

Tim

This is completely and utterly false.

Raid 5 does NOT use a dedicated drive for parity, the parity is distributed.

A failed drive would not affect the array at all.

Not sure how much experience you had with RAID, but at least dont give wrong opinions.

A 3 drive RAID5 array will yield excelent results.

---

