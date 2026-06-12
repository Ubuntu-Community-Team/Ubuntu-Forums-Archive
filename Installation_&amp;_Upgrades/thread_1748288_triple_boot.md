---
title: "triple boot"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by polska03 on 2011-05-03
I am pretty new to this and do not know the details of partitioning and every site I go to does not show very detailed instructions. Simply I keep getting blue screens with many different errors on my windows 7 computer and now I want to reformat the entire drive. I plan only installing Widows 7 again, ubuntu and linux mint(yes I know mint is pretty much exactly the same thing as ubuntu). My plan is to use a live cd of ubuntu and use the tool gparted to clear the entire hardrive. Then create 3 partitions(4 if you include the automatic dell recovery partition) around 40% windows, 40% ubuntu and 20% mint. I know windows used ntfs format and both linux distributions will use ext4 format. From there I do not know what to do, I do not want to run linux along side windows because this has caused me some problems. I was wondering if someone could recommend a detailed website on how to do this, or if someone can explain it to me?

Cheers

---

### Post by Joe of loath on 2011-05-03
What you have described is all you need to know. Other than that it's simple arithmetic to work out the partition sizes.

---

### Post by Megaptera on 2011-05-03
You're certainly on the right lines.
Here's a good guide for a dual-boot that you can tweak to a triple
[http://www.linuxbsdos.com/2010/05/26/manual-disk-partitioning-guide-for-linux-mint-9-and-ubuntu-10-04/](http://www.linuxbsdos.com/2010/05/26/manual-disk-partitioning-guide-for-linux-mint-9-and-ubuntu-10-04/)

To get around NTFS / Ext4 have you considered using a shared data partition? Useful guide here:
[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

Hope these are helpful?

---

### Post by perspectoff on 2011-05-03
Here's my preferences:

Kubuntuguide.info:

[http://www.kubuntuguide.info/index.php/Multiple_OS_Installation](http://www.kubuntuguide.info/index.php/Multiple_OS_Installation)

Ubuntuguide.org:

[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

---

### Post by oldfred on 2011-05-03
Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.

How much do you expect to use mint? If a lot you may want to leave home inside / (root)  for both Ubuntu & Mint and  create a /data partition. Then all your Documents, Music, Video and other data folders can be shared. You should not share /home as that has config settings that may be different between installs.

So instead of /home I would create another 20GB root for Mint and then use the rest for /data. I would still have a /shared NTFS partition for data you want to share between windows & Linux. If you want all or most of your data in the /shared NTFS then you may not need a /data. I have both and my /shared is now used very little and all new data goes into /data as I boot XP very little. I keep my root partitions small and include /home but aggressively move data into a data partition.

---

