---
title: "Installing 11.04 with manual swap on a Dell Laptop"
date: 2011-05-21
forum: Installation &amp; Upgrades
---

### Post by prahar on 2011-05-21
I am trying to insall 11.04. Here are my current computer specs

Dell Inspiron N4010
Intel Core i5 M460 @ 2.53 Ghz
4 GB RAM
64- bit Windows 7 Home Premium

I have a single HD with three partitions currently,

1. Primary Boot Partition for Windows - 475 GB (100 GB free)
2. Recovery Drive for Windows - 9.88 GB
3. OEM Partition - 361 MB

Now I shrank my primary volume giving the ubuntu installation drive around 30 GB (enough?). However, I am unable to make a swap partition because dell laptops apparently do not allow more than 4 partitions?

I read somewhere that it does not allow more that 4 primary partitions, but we can have more logical drives in an extended partition. I am totally confused about this. Is this possible? How do we do it then? Can a swap partition be a logical drive?

Also, I heard (I may be completely wrong) that there are some MBR issues when you install Ubuntu alongside Windows 7. What are these issues? And how would we go about fixing them?

Any help would be appreciated. Thanks a lot.

---

### Post by Quackers on 2011-05-21
I would suggest that you delete the new partition you have created for Ubuntu, leaving just the original 3. (Actually I would check that figure again as Dell is known for using all 4 primary partitions at times).
It is not Dell that limits the number of primary partitions, it is the MBR partitioning system that does that.
If you run the Ubuntu installer when only 3 primary partitions exist you should get the option to install alongside Windows 7. If you use that option the installer will create an extended partition, which will include an Ubuntu root logical partition and a logical swap partition.

---

### Post by Lateralis on 2011-05-21
It is entirely possible. =)  The limitation of 4 primary partitions is not Dell specific but a general limitation.  However, you can have almost as many logical partitions as you like in an extended partition.  (There is a limit of 255 logical partitions per extended partition I think, but not sure.)  

For information on partitioning, [this Ubuntu guide]("https://help.ubuntu.com/community/HowtoPartition") is particularly good.

So, what I would say, is that you will need to create an extended partition for the Ubuntu install, and then create as many logical drives as you want for Ubuntu.  Very basically, that would be one partition for the root partition ('/') and one for swap.  More extravagant partitioning schemes can be used, where you have a separate /home partition (that is recommended but certainly not necessary), separate /usr/local, /var etc...  If you're just getting your feet wet with Ubuntu, then probably stick to a root and swap partition first.  

As for the size of these partitions, the / doesn't need more than about 25-30 GBs.  However, how much space you need depends on how you are going to use your computer, i.e. if you have a separate / and /home directories, if you're going to have a "shared" partition between Windows and Ubuntu, where you will store things like your music, photos and so forth.  

As for the MBR, there shouldn't be any issues, per se.  When you install Ubuntu you will install the Grub (Grand Unified Bootloader) into the MBR.  Grub will allow you to boot into Windows and Linux by giving you a menu when you boot.  However, Grub with all of its configuration files are too large to be stored in its entirety on the MBR, so its critical configuration files are stored in the /boot/grub directory in the Ubuntu installation.  If you wipe Ubuntu off for whatever reason, then you will have a broken Grub - it will look for files that simply do not exist any more.  So, if you decide you want to wipe Ubuntu and go back to Windows only, you should reinstall the Windows bootloader first.  That is the only stumbling block that I can think of.  Otherwise, Grub and Win7 work fine - I dual boot between Ubuntu 10.04 and Win 7 on this very machine in fact!  

Hope this all helps. =)

---

### Post by mohloko on 2012-06-27
I spend hours looking for a solution this helped me a lot. I will try tomorrow
thanks =D

---

