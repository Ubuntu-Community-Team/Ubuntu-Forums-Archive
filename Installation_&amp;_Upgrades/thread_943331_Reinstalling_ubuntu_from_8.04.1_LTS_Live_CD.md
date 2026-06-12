---
title: "Reinstalling ubuntu from 8.04.1 LTS Live CD"
date: 2008-10-10
forum: Installation &amp; Upgrades
---

### Post by texas.chef94 on 2008-10-10
Be advised the following description of my present partitioning configuration is the result poor choices on my part, creating too many partitions and then attempting to recover with a resulting mess. Obviously I can still dual boot and both OS work fine, but I would like to have my partitioning correct.
Partition      Size      Used                  flags
ntfs        20003MB   10199MB                  :confused:Boot      (unmounted)???
Free space  1003MB                                    (was swap extra)
Ext3        16878MB   3800
Free space  789
Ext3        485       155
swap        838       -0- MB

With the live CD in I am forced to choose manual partitioning and I can delete and edit but I end up with no root system defined to reinstall and this is way beyond my limited comprehension.

Finally if it helps I did a df -h and results
ilesystem            Size  Used Avail Use% Mounted on
/dev/sda7              16G  3.4G   12G  23% /
varrun                617M  160K  616M   1% /var/run
varlock               617M     0  617M   0% /var/lock
udev                  617M   68K  617M   1% /dev
devshm                617M     0  617M   0% /dev/shm
lrm                   617M   39M  578M   7% /lib/modules/2.6.24-19-generic/volatile
/dev/sda5             455M  141M  297M  33% /media/disk

I know there is someone out there to solve this mess I created, but is my comprehension up to the task? I sure will give it shot and appreciate your time and effort.
Looking for rationalization, maybe being 76 a retired chef and too damn curious.

---

### Post by Elfy on 2008-10-10
When you get to the partitioning part of the install choose manual again. I assume you want to reinstall over the original buntu installation.

Pick the partition and then edit partition - you will get a new screen, in the use as menu pick use as ext3 (might be labelledas ext2 journalled) - tick the format box, in the mountpoint menu pick /

Close that window and you should now see that the partition has a mountpoint of / against it.

If there is anything that you wnat to do to the partitions, run this from a terminal in the livecd and post it here with what you actually want to do to the partitions. IF you want to remove and reallocate the free spaces we can do that.

```
sudo fdisk -l
```

---

### Post by texas.chef94 on 2008-10-10
Foresrpixie I thank you for your interest in helping me and in the interest of my finally getting this right might I pose several questions before I launch the re-install.
1. What about those free spaces that are actual partitions. When they are deleted is not thar minimal free space still a partition?
2. My research indicates I might be wise in creating a home partition as well.
3. Does it make a difference that XP or ntfs has that boot identification under flag and is unmounted.
4. Finally what I would like to end up with is a minimal ntfs partition i.e. as little size as possible. a 1 GB Swap and a 1 GB home partition with the remainder Ext3 for Linux.
Unless you find something wrong with this configuration.
Awaiting your reply to get this show on road and thanks

---

### Post by lumilanis on 2008-10-10
Hello everybody!

I had already installed Ubuntu 8.04 LTS and it worked fine as dual boot with my x64 XP. I just needed to instal grub boot loader manually after Ubuntu installation completed.
After that, I don't know a reason, I boot from my XP to check if everything is OK, and after coming back to Linux boot, everything seems OK, it starts with logo, and boot progress bar don't appears, I just see bar turning from left to right and contrary over and over...
Do you have an idea why I'm having this problem?

Addition. Both OSs are installed on IDE 40GB hard drive.
XP is on first NTFS partition (20GB) and Ubuntu is on Second Ext2 partition (10GB) and in has 2GB swap partition. Rest of HDD I'm using under XP as NTFS for additional security data backups.

Grub boot loader is installed on (hd0) and it's pointer for Ubuntu is on (hd0,4) and everything was OK until now.

Thanks in advance!

---

### Post by Elfy on 2008-10-10
@lumilanis - please start a thread of your own, this thread is unlikely to be of any use to your problem.

@texas.chef94
> 1. What about those free spaces that are actual partitions. When they are deleted is not thar minimal free space still a partition?No, once you have deleted them they will be unallocated spaces within the hdd.

> 2. My research indicates I might be wise in creating a home partition as well.I also used to do this, now though I have a small /home that gets used for system configs. All of my data is kept on seperate partitions and drives.

> 3. Does it make a difference that XP or ntfs has that boot identification under flag and is unmounted.Not that I'm aware of no - your xp wouldn't be mounted when the linux is running, you can though have the drive available if there is data on there you need to access from ubuntu

> 4. Finally what I would like to end up with is a minimal ntfs partition i.e. as little size as possible. a 1 GB Swap and a 1 GB home partition with the remainder Ext3 for Linux.This is fairly simple to achieve and can be done from the livecd. It will make life much simpler if you can post the result of the command I gave in post#2. I am though a tad confused with your statement that you want a seperate /home but only 1Gb - from the information you gave, root is ~16Gb and you alos wish to shrink the xp so it's likely that we can do more with your partitions.

So to summarise we need the result of ```
sudo fdisk -l
```, it will also help to know how big the xp partition is and how much spare there is from it before we can point you in the right direction.

While you are in xp getting the information please defrag at least twice before you try to work with partitions.

Furthere, as you are going to be working with partitions - make sure you have good backups of anything you can't afford to lose.

---

### Post by texas.chef94 on 2008-10-10
I was vague in several areas and I corrected that in posting to a kubuntu forum and immediately received a fix based on what I did not happen to share here. At any rate I than everyone and my re-partitioning has been solved. How fortunate I am to have such a great resource

---

### Post by lumilanis on 2008-10-11
OK, sorry, I'll do it in a future...
I already solved my problem by reinstaling all over again.

Reggards!

---

