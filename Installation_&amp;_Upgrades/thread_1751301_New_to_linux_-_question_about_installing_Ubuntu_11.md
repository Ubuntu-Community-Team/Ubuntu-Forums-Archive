---
title: "New to linux - question about installing Ubuntu 11.04"
date: 2011-05-06
forum: Installation &amp; Upgrades
---

### Post by Bane99 on 2011-05-06
Hey guys, completely new to linux and ubuntu.  I was told by another  person to try peppermint OS or Crunchbang, but seeing as I've never used  linux before I thought I'd try out Vanilla Ubuntu first to get a feel  for it.

The issue i'm having is determining which drive to install Ubuntu and where to install the bootloader.

Current setup: 2 HDD - stats as windows 7 reports

640 GB Drive[INDENT]C: 540GB: size 498GB used 149 GB Windows 7 Pro x64
D: 99MB: size 99MB used 28.7MB - Reserved for ^
E: 100GB: size 97.6GB used 217MB - Free
[/INDENT]F: 500 GB Drive: size 465GB used 86.5GB - Steam games and backup

After  loading up the CD, for installation I chose the other installation  option to choose the location for installation, I get the following:

/dev/sda[INDENT]/dev/sda1 ntfs size 500105MB used 92844MB
[/INDENT]/dev/sdb[INDENT]/dev/sdb1 ntfs size 104MB used 35MB
/dev/sdb2 ntfs size 535170MB used 159904MB
/dev/sdb3 ntfs size 104855MB used 3221MB

[/INDENT]Device for boot loader installation:

/dev/sda ATA WDC WD5000AAJS-0 (500.1GB)
/dev/sda1 Windows 7 (loader)
/dev/sdb ATA WDC WD6400AAKS-2 (640.1GB)
/dev/sdb1 Windows 7 (loader)
/dev/sdb2
/dev/sdb3

So the big question is, in which drive do i install ubuntu?  I'm thinking /dev/sdb3
And at what location should i install the boot loader?

Thanks guys!


Separate Question
Specs:
i7 920
Gigabyte GA-EX58-UD5
6 GB DDR3
eVGA GTX 285
SB Audigy 2 Platinum - Speakers
Realtek Onboard Sound - microphone
Onboard LAN
Blue-Ray Drive
DL DVD-RW Drive

Think there will be any driver issues?

---

### Post by Megaptera on 2011-05-06
Can't advise on your question but I have a suggestion for you ... 

If you browse this forum, you'll see that 11.04 being very new and with a new user interface (Unity) still has some issues.

As you're new to Ubuntu I'd suggest 10.04 as it's more stable & therefore less problematic.

---

### Post by Bane99 on 2011-05-06
Regardless of version installation, can anyone help me concerning drive selection for installation and boot loader installation location?  I'm pretty sure it's /dev/sdb3, but the boot loader installation i'm not sure where I need to install it. Thanks :)
Also, 32bit or 64bit?

---

### Post by Quackers on 2011-05-06
Grub is installed to the mbr of the hard drive that you install Ubuntu on (that would be /dev/sda if you installed Ubuntu to the partition /dev/sda4 for example).
However you seem to have 2 hard drives. The first is 640GB and is fully partitioned.
The second is 500GB and 465GB appears to be partitioned. 
Do I read that correctly?
If I'm right then you should have approximately 35GB unallocated space at the end of the 500GB hard drive.
Ubuntu could be installed in that unallocated space. You cannot install Ubuntu as a dual boot system to a partition formatted as NTFS. Ubuntu needs a EXTFS type partition.

---

### Post by Bane99 on 2011-05-06
sda - 500GB drive - Steam Games and Backups[INDENT]Used: 86.5GB
Free: 465GB
[/INDENT]sdb - 640 GB Drive[INDENT]Partitions = 3
Partition 1 - Windows 7 Pro x64
Partition 2 - Windows reserved
Partition 3 - Free ~ 100GB

[/INDENT]I can always format the third partition there to EXTFS.  I left it blank for the purpose of installing linux or another OS, although in hindsight, 100GB is a lot.
Given the info I have in the first post, is that third partition sdb3?  It can be partitioned again if needed.  Also install the boot loader to sdb3 if I choose to use that partition for ubuntu?

The real question is, what would be the best thing to do in my current situation?  Thanks.

---

### Post by Dutch70 on 2011-05-06
For us to give you the best answer, boot up the live cd & take a screenshot of your partitions for both hdd's in Gparted. You can click the box in the upper right corner of gparted to see the other hdd. 

Please attach the screenshots to your next post using the paper clip in the tool bar.

Edit: You don't install the bootloader to a partition, such as sdb3. You either install it to sda or sdb.

---

### Post by Bane99 on 2011-05-06
Attached is the image.
I thought I had typed it all out.  Hope this helps.

---

### Post by Dutch70 on 2011-05-06
Installing to sdb3 would be fine. Format it to ext4. Set the mount point to "/" aka "root"

You'll also need a swap partition equal to, or slightly larger than your physical RAM. 
You can shrink sdb3 to leave unallocated space to create your new swap partition. Format it to "swap"

---

### Post by oldfred on 2011-05-07
Some like to have all their systems on one drive and data on the other. I prefer to have each drive have at least one system, so if one drive fails I can boot the other. 

Some win7 programs hide DRM info in the same sectors just after the MBR as grub wants to install additional boot code. Grub2 has fixed it for flexnet in sector 32, but some others exist. So if you have two drives it can be better to have grub2's boot loader in the other drive.

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

I like to create partitions in advance with gparted from the liveCD or from a gparted liveCD.
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")

Great guide for second drive - lots of detail still based on 10.10, but differences are most cosmetic.
Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by yavamoni on 2011-05-25
> **Dutch70 said:**
> 
Edit: You don't install the bootloader to a partition, such as sdb3. You either install it to sda or sdb.
But the 11.04 install *asks* for the boot loader location, and *offers* a choice, for either the drive or each partition. 

I understand previous versions installed the boot loader into the same partition the system was installed to. Does one have to manually select that now?  What happens if one selects a partition where a previous boot loader is already installed? 

Or should one install it to the main drive?

---

### Post by Quackers on 2011-05-26
Grub is normally installed to the mbr of the disc (as in /dev/sda or /dev/sdb) not to a partition. The installer defaults to /dev/sda, which is the first drive found.

---

