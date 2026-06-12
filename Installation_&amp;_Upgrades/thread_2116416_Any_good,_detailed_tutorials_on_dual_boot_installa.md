---
title: "Any good, detailed tutorials on dual boot installation?"
date: 2013-02-15
forum: Installation &amp; Upgrades
---

### Post by ChrisInNevada on 2013-02-15
Hi, I am a newbie here.  I have windows 7 loaded and want to install Ubuntu 12.04 and create a dual boot.  I've never done this before.  Does anybody know here can I find a good tutorial that covers the elements and recommendations for installing, partitioning and partition size, etc?  

Also, I need the highest level of security I can establish.  If anyone has any recommendations there regarding firewalls and anti-virus, that would be helpful too.  Thanks!

---

### Post by MAFoElffen on 2013-02-15
> **ChrisInNevada said:**
> Hi, I am a newbie here.  I have windows 7 loaded and want to install Ubuntu 12.04 and create a dual boot.  I've never done this before.  Does anybody know here can I find a good tutorial that covers the elements and recommendations for installing, partitioning and partition size, etc?  

Also, I need the highest level of security I can establish.  If anyone has any recommendations there regarding firewalls and anti-virus, that would be helpful too.  Thanks!

I've been around the block... I've lead people through this.

Before recommending details. It would be nice to know what hardware it is going on... You can get those details from Win7:
CPU
RAM Size
Exisitng partitions and how much of it is actually used now.
Video GPU

Basically, Windows OS'es like to be near the top of the partition tree. That's where they run best. Linux doesn't care where it run's from.

Even though WUBI is a viable option for users, installing WUBI as started from Windows and running it in an image file... I stay away from and install as separate OS, safeguarded in separate partions. Faster and safer that way. Then you can use it to rescue Windows if needed.

Decide on a boot manager. Default for Ubuntu is Grub2. Very powerful and easy to install. Option is to use the Win boot manager, but not as easy to setup and maintain (manually). I recommend Grub2.

After you research on the partitions and would size you might have left to play with, plan out your partitions. In linux the numbering scheme goes as such, first disk is sda, second sdb, etc... You have 4 primary partitions that you can create on a disk. Or you can have 3 primaries and logicals. Logical partitions are spec'ed differently and are unlimitted in quantity.

Linux partitions are ID'ed as sda1, sad2... First Logical partition on a disk is sda5.

Ubuntu is usually installed in sda5, with what is called a linux swap partition in sda6. A linux swap is like a windows swap file. If you need more memory than you have, it will page to the swap partition. If you herbernate or put the system to sleep, it copies the whole desktop and progam states to that swap space, to retrieve it on wake-up. So the usually size for a linux swap is the size of your RAM times two.

So windows partitions can be moved and shrank. This is better done from inside Windows. You can do it from Linux, but the first time you start up Windows, it will find that it's indexes would need to be repaired. Don't add to your workload.

Move the start of the first windows partition 1MB from the beginning and leave that free space unassigned. That leaves enough room for the boot loader to load without having to worry about it overwriting or overlapping the start of the first partition.

After you shrink down your windows partition(s) and get organised... Boot from the Ubuntu install disk. Answer the questions as a normal install until you get to the partitioning menu. Donot select "use whole disk." That of course would overwrite your windows install. Under that is "use free space." That would automatically calculate the free space left and do everything for you.

The option under than is "custom/manual". Use that if you know what sizes you want where and of what types. This is very handy if you are installing to other than the first disk and/or are tuning the system.

The install will continue until near the end it will probe the system and search for other OS'es. It should find Windows 7. It will then ask you if you want to install grub2 as your boot loader. If you are going to use the Windows Boot loader, you would say no. If you are using Grub2, it will install and configure itself.

On install finish, it will ask you to remove the disk and press enter to restart... There's a few thing you might need to know before this... If you have spacial vido (ATI or NVidia) there is a few things you need to do on restart so you have graphics long enough to install their appropriate drivers. If not special video, you're done.

Good as basic start?

Oh, I use Clam AV for antivirus and ufw for the firewalls. I install Avaste antivirus for some customers.

If you post the info asked for, I or someone else can fill in some of the details.

---

### Post by Sef on 2013-02-15
For an excellent tutorial, check out [Psychocat's]("http://psychocats.net/ubuntu/installing") site.

---

### Post by OrangeCrate on 2013-02-16
Additional instructions on dual booting can be found here:

[http://ubuntuguide.org/wiki/Ubuntu_Quantal_Installation#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu_Quantal_Installation#Dual-Booting_Windows_and_Ubuntu)

Enabling the "Uncomplicated Firewall" instructions can be found here:

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

