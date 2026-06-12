---
title: "New dual-boot installation on fakeRAID"
date: 2011-01-13
forum: Installation &amp; Upgrades
---

### Post by azmodi on 2011-01-13
Hi

In the hope of avoiding a few problems, I thought it would be a good idea to seek some advice before I go ahead with my planned Ubuntu installation.

I've been monitoring the progress of Linux over several years and, when I built my latest PC last year installed two RAID1 arrays with the intention of installing Ubuntu on one of them. Win7 is already installed on the other array, and the idea is to dual boot them. My PC uses an Asus M4A89GTD PRO / USB3 motherboard with a AMD SB850 chipset supporting 'fakeRAID' configured through the BIOS.

 I've not installed or used Linux before, so simple explanations would help, if possible!

According to my research so far, it seems that the installation of Ubuntu on a fakeRAID array should now be easy / easier, since (to quote the [Lucid Lynx Release Notes]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes")) *'Dmraid "fake raid" devices are supported out-of-the-box on the Ubuntu 10.04 LTS Desktop CD, and are detected and activated by dmraid on boot. Ubiquity will offer to install on the RAID array, and not on the RAID members.'*

Q1)
Does this mean that the tutorial at [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) is entirely superseded, and that it's statement that *'FakeRAID is not supported by Ubuntu'* is now entirely incorrect? Or are there still some special steps / precautions to look out for? I can't find any updated guidance since this change - just plenty of dire warnings pre version 10.04.

Q2)
The 'spare array' is already partitioned since I've used it for some other purposes. Other than reformatting one of the partitions from NTFS to ext4 for Ubuntu, are there any other considerations? For example does Ubuntu insist on being installed to the first partition / not on a logical partition?

Q3)
Since Win7 and Ubuntu would keep their own arrays (other, perhaps, than putting their swap / page files on the opposite array for a little added performance), what is the best method for dual booting them - and how and where should the software be installed?

Q4)
Is it likely that this installation would require any special precautions when upgrading to future versions?

Q5)
What else should I be thinking about?

Thanks in advance for your advice...

---

### Post by ronparent on 2011-01-15
Q1)
Ignore the fakeraidhowto since it has never been updated for 10.04 or 10.10. The issue now, especially with 10.04, is that gparted has a bug in that it won't see the raid drives as a raid. To work around for an install, simply boot to a live cd for the desktop edition, and install kpartx. That will allow gparted to work normally as long as the session is active - thus allow the partitioning step to proceed.

Q2) By electing to manually partition in the partitioning step when that option is offered, you can select any partition to format and install to. With Win 7 you may already be in danger of exceeding a four primary partition limit because of partitions already created. Simply choose to install to an extended partition. I can see why you might have a spare partition, but, I don't know what you mean by a spare array unless you have four actual physical drive in your box.

Q3) In most modern systems with the order of 2Gb or more of RAM, except for windows I would see little practical advantage of putting the linux swap on a separate array. Prior to win 7 I always kept the swap/page files on a separate physical drive from the OS itself to minimize fragmentation but i no longer feel the need for it.

Q4) 
Only if you don't prudently back up your data on a regular basis. You can set up a separate /home partition to ease a future upgrade or reinstall. But risks still make a good backup plan prudent.

Q5) 
We would probably never know until it happens.:P

Just proceed cautiously, as you are, and post if you get into trouble. Good luck.

ps: Welcome to the forum.

---

### Post by azmodi on 2011-03-14
Ron

Thanks for your reply back in January, and your good advice.

I was anticipating that getting Ubuntu installed might take a little time, so left it a few weeks until this last weekend when I had some spare time. I have to say I needn't have delayed, since it only took a couple of hours and everything went smoothly, apart from it taking me a few minutes to figure out that I needed to specify a mount point.

Incidentally, re your puzzlement over point 2, I do indeed have 4 physical drives configured as 2 separate arrays...

Anyway, thanks once again. :grin:

---

### Post by ronparent on 2011-03-14
Glad to hear it is all worked out. Have fun.

---

