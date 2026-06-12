---
title: "Installing Ubuntu 10.10 with multiple hard drives?"
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by theblah on 2010-12-27
Hello :)
I have been trying to install Ubuntu on my new computer as a duel boot with Windows 7. My computer has four 1TB hard drives, One with Windows 7 installed, two that are used for storing media (both are independent, not in a RAID or anything like that) and one empty hard drive. This hard drive contains a 901.51 GB NTFS partition, and 30.00 GB of Unallocated space, I wish to install Ubuntu in this unallocated space; giving it 20 GB (the 10 GB left over might be used for installing XBMC Live)

But when I boot Ubuntu's Live CD the installer doesn't show me the unallocated space, and doesn't really show me any of the extra Hard drives. :-?

Could some one help me? 
I'll give you a cookie ;)

---

### Post by XeonBloomfield on 2010-12-27
You need to chose manual partitioning and select unallocated space and create here EXT4 partition with mount point "/". 

Now it will probably work.

---

### Post by Mark Phelps on 2010-12-27
The best results I've obtained, when faced with multiple drives, is alway to do the following:
1) Disconnect ALL drives but the one you intend to use for installing Ubuntu
2) Install Ubuntu to the one connected drive, including GRUB to its MBR
3) Reconnect the other drives -- but continue to boot from the Ubuntu drive
4) Boot into Ubuntu, open a terminal, and enter "sudo update-grub".  This should generate a new GRUB menu which contains entries for any other OSs on the PC.
5) Reboot

NOW, you should get a GRUB menu -- showing all the OSs and kernels it found.

---

### Post by oldfred on 2010-12-27
Mark Phelps' way avoids all the issues of being sure to install to the correct drive and makeing sure grub2 bootloader is in the same drive, so it is a good way.

Some more info on multiple drive installs. Dual applies to anything more than one.

Dual drive internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

I always prefer to partition in advance and then use manual install to choose which partition is root, /home and it autofinds the swap.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space.
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.

I have either Windows or a version of Ubuntu on every drive, but some want just a basic small system on any large drive.
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)

---

