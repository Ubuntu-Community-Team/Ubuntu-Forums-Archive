---
title: "Installing ubuntu 11.10 on external hard drive"
date: 2012-03-28
forum: Installation &amp; Upgrades
---

### Post by Hitokirikenryu on 2012-03-28
I have a freshly formatted external hard drive and I want to install ubuntu 11.10 on it. I current have ubuntu installed on my win 7 hard drive with wubi and I do not want to really use it to fully explore ubuntu since it's not really designed to be used that way.

I have searched around instructions and haven't found a clear cut answer on how to do a clean install of ubuntu 11.10 on a external drive. I do not want to risk messing up the mbr on my main internal drive. I am downloading the iso file for ubuntu 11.10 right now and hope to get a full install running soon...

---

### Post by Brizvegan on 2012-03-29
Hi,  
Check out this illustrated tutorial as an example:
[http://www.linuxbsdos.com/2012/02/20/install-ubuntu-11-10-on-external-hard-drive-with-an-ntfs-partition-at-the-end/](http://www.linuxbsdos.com/2012/02/20/install-ubuntu-11-10-on-external-hard-drive-with-an-ntfs-partition-at-the-end/)    

You don't have to have a /boot partition if you don't want to.    
You could just have / and swap. 
 Or /, swap and /home. 
Up to you.

---

### Post by bcbc on 2012-03-29
Here's a guide... it's based on 10.10 Maverick Meerkat but the installer hasn't changed significantly and the guide is very thorough: [http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by oldfred on 2012-03-29
I have always liked Herman's instructions as linked by bcbc, but some new users find them too much (detail). But he has the important detail highlighted of where to install the boot loader. You have to install it to sdb or whatever device the external is seen as. Many suggest unplugging internal drive but if portable or you are not comfortable unplugging drives you do have to install grub correctly. 

p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

Brizvegan linked instructions also mention choosing sdb, but does not highlight it quite as much. But I do not think you need the separate /boot for a desktop install. But I do prefer the choice of an extra NTFS partition for shared data with Windows. Best not to write into the Windows 7 system partition. 

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by Hitokirikenryu on 2012-03-30
Thanks bcbc, that is exactly what I was looking for! I will definitely install ubuntu once I get another external drive. The one that I currently have has a few bad sectors, and I don't need it to crash again...

Herman's walkthrough does not go into file system choice too much, so does it have to be ext4 by default? I have never heard of these other file systems for ubuntu so I don't know anything about them.

Another question, what size swap partition should I make? I have 9GB of RAM installed?

---

### Post by bcbc on 2012-03-30
I always use ext4. That should be the default as well. I confess I don't know a lot about the newer btrfs but from glancing at various posts since it came out... it seems it's had a few issues (not unusual for a new fs I guess). Here's a comparison that looks like ext4 performs better: [http://www.phoronix.com/scan.php?page=article&item=linux_33_btrfs&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_33_btrfs&num=1)

In terms of swap, it depends on whether you want to hibernate. If you do, I generally make swap = size of RAM + 500MB. Probably as RAM gets bigger the + 500MB can get smaller, but e.g. on my old beater with 1GB RAM it wouldn't always hibernate so I doubled it for swap. 
I've never seen an exact formula for sizing swap that allows hibernation, so I recommend erring on the plus size, rather than trying to be stingy.

If you don't want to hibernate, you probably don't need a lot of swap with that much RAM.

---

