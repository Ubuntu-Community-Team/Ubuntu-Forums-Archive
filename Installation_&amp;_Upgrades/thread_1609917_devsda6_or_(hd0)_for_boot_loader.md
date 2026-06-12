---
title: "/dev/sda6 or (hd0) for boot loader??"
date: 2010-10-31
forum: Installation &amp; Upgrades
---

### Post by freesparks on 2010-10-31
Hello all,

 This is the part of the installation that always confuses me.  I want to dual boot with Windows XP Professional and Ubuntu on the same internal hard drive.  I've successfully partitioned my internal harddrive and I am now at the Advanced Tab ready to install the boot loader in the final point of the installation process before all the Linux partitions are  written in stone..  Basically this is my set up:

> /dev/sda  ATA FUJITSU (75.4 GB) HARDDRIVE
/dev/sda1 
/dev/sda2     Microsoft Windows XP Professional
/dev/sda5     linux ext4 /boot
/dev/sda6     linux ext4 Ubuntu 9.10(9.10) /root
/dev/sda7     linux ext4  /home
/dev/sda8     linux ext4 swap
/dev/sda3     Windows fat 32 

Under the advanced options Tab by default the boot loader has (hd0), do I leave it as is if I'm installing Ubuntu on this internal hard disk with the configuration above or do i install Ubuntu on /dev/sda6 which is my root "/" directory..??  Any help on this would be greatly appreciated.

Best Regards,

freesparks

---

### Post by tommcd on 2010-10-31
> **freesparks said:**
> 
Under the advanced options Tab by default the boot loader has (hd0), do I leave it as is if I'm installing Ubuntu on this internal hard disk with the configuration above or do i install Ubuntu on /dev/sda6 which is my root "/" directory..??  

Just leave it at the default, which is to install grub2 to the MBR (master boot record) of your hard drive. In other words, let it install to hd0 (/dev/sda).

Just out of curiosity, what is on /dev/sda1? Is that a recovery partition or something?
You really should not need a separate /boot partition either. I boot 3 linux distros plus WindowsXP, and I have never used a separate /boot partition.
Write back if you need more help.

---

### Post by freesparks on 2010-10-31
Hello Tom,

   YES!!,,  That is the one I chose..  Thanks so much for your quick reply man, I really appreciate it.  And, yes, you are very intuitive, it is indeed a Windows recovery.  Thanks again.  I'll let you know how I fair out.  So with that said, had I specified /dev/sda, is that equivalent to (hdo)??    Because that, to me, is interpreted that it's (hd0) is saying, "here I am", I want to boot first, and /dev/sda is saying pretty much the same because it is in front of the entire hard drive!!

Best Regards,

freesparks

---

### Post by tommcd on 2010-10-31
> **freesparks said:**
>   So with that said, had I specified /dev/sda, is that equivalent to (hdo)??    
Yes it is the same. Grub calls the first hard drive (hd0).
The second hard drive is (hd1), etc. Partitions in grub2 start with 1. So the first partition (/dev/sda1) would be called (hd0,1). The second partition (/dev/sda2) would be called (hd0,2) in grub2, etc.
If you choose the default, which is to install grub2 to the MBR, you should not have to specify anything though.

---

### Post by freesparks on 2010-10-31
Thank you,

  So to confirm, I would gather all I need if I am installing everything manually, are:

/ or rather /root
/home
/swap or rather swap

Because, correct me if I'm wrong,  Ubuntuwill install in  the /home directory the /lib, /opt, /usr, /var, /tmp, and /boot directories, Correct??  Thanks again!!

Best regards,

freesparks

---

### Post by tommcd on 2010-10-31
> **freesparks said:**
> 
  So to confirm, I would gather all I need if I am installing everything manually, are:
/ or rather /root
/home
/swap or rather swap
Yes, the root, swap, and home partitions are all you really need. It is good to have /home on a separate partition because if you ever reinstall Ubuntu, then all of your data is safe on a separate partition.
> **freesparks said:**
> 
Because, correct me if I'm wrong,  Ubuntuwill install in  the /home directory the /lib, /opt, /usr, /var, /tmp, and /boot directories, Correct??  

The /lib, /opt, /usr, /var, /tmp, and /boot directories are not installed *inside* the home directory. If you install using 3 partitions (root, swap, and home) then the /lib, /opt, /usr, /var, /tmp, and /boot directories will all be sub-directories on the root partition.
If you installed using only 2 partitions (root and swap) then /home would also be a sub-directory on the root partition.
See this for creating a separate home partition:
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by freesparks on 2010-10-31
Why the install process nukes the GPARTED application is beyond me.  But, I would love to know if you advise me on nuking the /opt partition and combining it using the application, Palimpsest Disk Utility,  with the /home directory.  Or can I just boot from my CD drive to the 9.10 Ubuntu Disk, load Gparted and do it from there.  This is my Linux partition setup:

> 34 GGB extended
   Contains logical partitions

   /dev/sad5 ---4.0 GB Filesystem   *this is the /boot drive I incorrectly made!!*
   Linux ext4

   /dev/sda6 ---5.0 GB Filesystem  [QUOTE]this is the root drive that I wish I can allocate more space to!!   Linux ext4

  /dev/sad7 ---10 GB Filesystem  >  this is my /home directory  Linux ext4

  /dev/sda8 ---12 GB Filesystem   > this is my /opt directory that I would like to delete and combine with my home directory since I am limited in space  Linux ext4

  /dev/sda9 ---3.3 GB Swap Space
 [/QUOTE]Thanks again, i can't thank you enough!!

Best Regards,

freesparks

---

### Post by tommcd on 2010-10-31
> **freesparks said:**
> Why the install process nukes the GPARTED application is beyond me.  But, I would love to know if you advise me on nuking the /opt partition and combining it using the application, Palimpsest Disk Utility,  with the /home directory.  Or can I just boot from my CD drive to the 9.10 Ubuntu Disk, load Gparted and do it from there.  This is my Linux partition setup:

First off, Ubuntu 9.10 will reach end of life in April 2011:
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
Also, 9.10 will have older versions of programs. I would recommend going with 10.04 for long term support, or 10.10 for the newest stuff.
Second, there is no need to bother with Gparted or Palimpsest (which I had never even heard of before you mentioned it here). Just choose manual partitioning from the Ubuntu live CD and create 3 partitions: root, swap, and home. Read the psychocats tutorial I linked to in my last post. You can just delete any partitions you no longer want. Then just create new partitions in the unallocated space that will be left after you delete the unwanted partitions.
I don't know how you ended up with a separate /opt directory. Your first post did not include that in your partition list.

---

### Post by freesparks on 2010-10-31
Man, you've been a great resource. Yes, the first thing I did was upgrade to 10.04, however upon doing so I was not able to boot on the new kernel, 2.6.31, whatever it is now.  I had to revert back to my older one.  I think this was caused by the fact that I did not have enough space.  Wish I could have researched it some more, and been more specific but this is not my system and I am doing this for a friend.  I will let you know how I fair out.  I created the /opt directory manually, but in having to reinstall and start from scratch, I just configured my system with a :

/home
/root
/swap

Does the order in which I do this matter?  Because I noticed I could not do it as Primary, and had to do everything Logical with Ext4, as I've been thought to do it. See when I think of /boot, in coming from the Windows World I think of blue screens and the /boot disk, completely different concepts and definitely not efficient as Unix.

Best Regards,

freesparks

---

### Post by tommcd on 2010-11-01
> **freesparks said:**
> ... I think this was caused by the fact that I did not have enough space.  ... I just configured my system with a :
/home
/root
/swap

These 3 partitions are fine. Delete the /boot and /opt partitions. Using 4GB is way to big for just a boot partition anyway. If you were going to use a separate boot partition, you only need to allow about 100-200MB for it. Using 8-12GB is way to big for an opt partition. Meanwhile, your root partition is a bit small. This is likely why you were short on space. Since you have 34GB allocated for linux, I would create a 10-12GB root partition, a 1GB swap, and the rest for home. If you plan to suspend to memory, then create a swap at least as large as the amount of memory you have. Otherwise 1GB is plenty for swap.
FYI: You can free up a bit of hard drive space by running:
```
sudo apt-get autoclean
```
You can free up a bit more space by running:
```
sudo apt-get clean
```
See "man apt-get for the details:
[http://linux.die.net/man/8/apt-get](http://linux.die.net/man/8/apt-get)
> 
clean
    clean clears out the local repository of retrieved package files. It removes everything but the lock file from /var/cache/apt/archives/ and /var/cache/apt/archives/partial/.
autoclean
    Like clean, autoclean clears out the local repository of retrieved package files. The difference is that it only removes package files that can no longer be downloaded, and are largely useless. This allows a cache to be maintained over a long period without it growing out of control.

> **freesparks said:**
> 
Does the order in which I do this matter?  Because I noticed I could not do it as Primary, and had to do everything Logical with Ext4, as I've been thought to do it. 
The order of the partitions does not matter. You have Windows partitions at the beginning of the drive anyway.

How many primary partitions do you have? You should be able to have 3 primary partitions and the rest as logical. No need to worry though. Linux runs just fine from primary or logical partitions.
Write back if you need more help.

---

