---
title: "NTFS Partition Unaccessible"
date: 2005-09-29
forum: Installation &amp; Upgrades
---

### Post by ivanjo10 on 2005-09-29
Hi,

I have a 80GB HDD divided into 3 partitions.
1. partition -primary (MBR) contains a WinXP instalation (NTFS) - 25GB
2. partition - logical drive on extended partition with all my data (NTFS) - 50GB
3. partition - ext3 - 5GB

And on a second HDD i have a 512MB Linux Swap partition.

I installed Ubuntu 5.04 last night. I mounted / on my ext3 partition (it was empty and fresh formated) and SWAP was on the secound drive. When asked do i want to install the GRUB to the MBR I said no and typed in hda4 (It was a mistake, as i later found out).

When I booted to windows my D disk (50GB, NTFS) became unusable. When I try to acess it Windows says that it is not formated. The disk manager says that it is a healthy RAW partition and partition magic says that it is a NTFS logical drive with 49999MB used out of 49999 in total and that it has a error 1541 - bad file record size. 

My guess is that the grub was installed to this partition instead of the ext3 and it overwrote the boot record or something like that. 

I'm desperate (all my data was on that partition) and I admit that I'm an idiot for not backing it up.

PLEASE HELP! What can I do to get the data back???

---

### Post by KingBahamut on 2005-09-29
Parition table and or the Maint. Partition might be screwed up. Actually most likely it is. Specially if Grub tried to install on that parition. Hmmmmm....there really isnt an "easy" way to fix this. How mission critical is the data? I can try to walk you through some steps to try to get to it, but they take time and a lot of patience. 
I try to help you if I can. You can msg me , It will take more than I can cram into a post on the forum.

---

### Post by dbott67 on 2005-09-29
There is a free Windows utility called [PC INSPECTOR File Recovery 4.x]("http://www.pcinspector.de/file_recovery/uk/welcome.htm") that I have used on occasion to recover hosed partitions & deleted files.  It works very well & it's absolutely free.

You could also try to repair the MBR.  Boot from your XP install CD, select REPAIR (to get to a command prompt) and then type fixmbr.

In normal circumstances, the fixmbr command will repair the master boot record of the primary drive, but in your case I'm not sure if it will be any help.  The downside to using fixmbr is that it blows away grub, which means that you won't be able to boot into Ubuntu (you'll need to re-install grub or re-install ubuntu).

-Dave

---

### Post by KingBahamut on 2005-09-29
fixmbr from the repair set on a 2000/XP cd is effectively the same as running fdisk /mbr. It might kill the mbr and that might cure the problem, but im more curious about what happened to the drive first before I go half cocked on the idea that nuking or hitting the MBR could fix the problem.

---

### Post by ivanjo10 on 2005-09-30
Hi everyone,

I just wanted to let you know that I managed to retrieve the data using GetDataBack. I booted linux but when I tried to mount the drive i got the message that there is a file system error (i managed to mount my other NTFS partition without any problem). So I installed GetDataBack under XP and got back all the data! 

Thanks for your time and help anyway!

---

### Post by kanishi on 2007-11-09
> **ivanjo10 said:**
> Hi,

I have a 80GB HDD divided into 3 partitions.
1. partition -primary (MBR) contains a WinXP instalation (NTFS) - 25GB
2. partition - logical drive on extended partition with all my data (NTFS) - 50GB
3. partition - ext3 - 5GB

And on a second HDD i have a 512MB Linux Swap partition.

I installed Ubuntu 5.04 last night. I mounted / on my ext3 partition (it was empty and fresh formated) and SWAP was on the secound drive. When asked do i want to install the GRUB to the MBR I said no and typed in hda4 (It was a mistake, as i later found out).

When I booted to windows my D disk (50GB, NTFS) became unusable. When I try to acess it Windows says that it is not formated. The disk manager says that it is a healthy RAW partition and partition magic says that it is a NTFS logical drive with 49999MB used out of 49999 in total and that it has a error 1541 - bad file record size. 

My guess is that the grub was installed to this partition instead of the ext3 and it overwrote the boot record or something like that. 

I'm desperate (all my data was on that partition) and I admit that I'm an idiot for not backing it up.

PLEASE HELP! What can I do to get the data back???

 I was same problem as you. But don't fear, you are **fix boot sector** only. Using **Partition Table Doctor** in Hirent's boot CD. Very simply :KS

---

### Post by karatchov on 2007-11-11
This seems like my problem ..
I had windows xp, ubuntu 7.04, with vista boot loader combined with easybcd and grub (on ubuntu partition)

When i tried to install new version of ubuntu (7.10) on a new partition, I thought it may be smart to install grub to the new partition, and use the vista boot loader by easybcd to config it (the way I did on the first time)

but, when installing grub, I typed setup(hd0,4) without even knowing which partition it was.

the next reboot, grub console prompted !!
so I used the xp install cd to fixmbr and reboot correctly on xp, but ...

my partition D: (90 GB of data) was inacessible, and partition magic show an error !!!

explorer ask to format the partition !

man I can't beleive that !

I hope the Partition Table Doctor will help me, otherwise I'am screwed ...

                                                        ...to be continued

---

### Post by karatchov on 2007-11-11
Thanks Kanishi, you just saved my *** :)

Nothing is more terrifying than seeing all your data disappear by one touch !

I had a bad memory of data loss, and this times, it scared me a lot ...

Well, the task seemed very easy, I managed to get Partition table Doctor, installed it and from the first run, it asked to fix an error onPartition 3 by chosing fixboot, one click, and the partition is back on explorer without the need to reboot :lolflag:

I will use grub next time with more precaution, maybe I will just install it on the MBR and leave it to manage all partition

---

