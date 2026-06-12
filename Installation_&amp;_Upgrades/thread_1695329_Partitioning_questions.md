---
title: "Partitioning questions"
date: 2011-02-25
forum: Installation &amp; Upgrades
---

### Post by TCMGO on 2011-02-25
I have read a number of articles on how to partition for dual booting, all quite helpful, but it still leaves me with a few questions:
 
1. Will one swap partition work under both Windows and Linux operating systems in a dual boot setup (I am using XP & Unbuntu)? How do these OS's recognize and use the one partition? Is there something that needs to be done at installation that causes both OS's to see and use the one swap partition or is it automatic? 
2. Since I am putting only the two operating systems on one hard drive, how should my seperate settings/programs/data drive (to be shared by both Ubuntu and XP) be best partitioned, if at all?

---

### Post by oldfred on 2011-02-25
Swap is only used by Linux systems, not windows. It has its own file inside the windows partitions for the same purpose. Some using Ubuntu also use a file in the / (root) partition, but that is not as standard.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

I share with XP but have each system on a separate drive. I also when first converting to Ubuntu created a shared NTFS partition for Firefox & Thunderbird profiles. I was trying to learn Ubuntu and my wife wanted to check e-mail or Internet with bookmarks from windows and I had to reboot. Once I created shared we did not boot windows nearly as often. I still have one app in windows, but I think I have just about weaned myself from it.

Shared NTFS partition 
[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

