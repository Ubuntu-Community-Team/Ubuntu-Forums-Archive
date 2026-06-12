---
title: "install Ubuntu on 2nd HDD"
date: 2010-11-11
forum: Installation &amp; Upgrades
---

### Post by kingdm on 2010-11-11
Hi there.

I have a 2 SATA HDD on my machine. The first one (320GB) contains the NTFS partition for my Windows 7. Now I have this second HDD (320GB), I want to install Ubuntu with it so I decided to create two partition with it, 50GB for Ubuntu and the rest for NTFS, so now I have two partition on it. 

I created an Ubuntu 10.10 bootable on my USB stick, booted it from there. Now on the installation, I set to manually assign partition, the installer detects my 2 HDD, the data was as follows

/dev/sta ATA ST3 - my first HDD contains Windows 7
/dev/sta1 320GB
/dev/stc ATA ST3 - my second HDD contains two partitions
/dev/stc1 50GB
/dev/stc2 230GB

Now I want to install Ubuntu on stc1 which is a 50GB partition, I changed the 50GB partition to ext4 journaling file system then checked the format drive. When I click forward, there was an alert asking me that I don't set any swap space. What is that? How can I set it? Is that really necessary? And also I am wondering on the another option below the boot loader installation which should I choose on there? its default choice was the /dev/sta1 which is my Windows 7 loader.

Anyone with inputs? :(

Thanks, really appreciated your inputs.

Regards.

---

### Post by oldfred on 2010-11-11
Another thread with lots of discussion. And yes you should have some swap, I suggest 2GB in a partition.
[http://www.uluga.ubuntuforums.org/showthread.php?p=10047142](http://www.uluga.ubuntuforums.org/showthread.php?p=10047142)

You need to be sure to install grub to the second drives MBR.

Some examples of installs:
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

See above for Maverick screens as they are somewhat different than Lucid was.
Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

---

### Post by PGHammer on 2010-11-11
> **oldfred said:**
> Another thread with lots of discussion. And yes you should have some swap, I suggest 2GB in a partition.
[http://www.uluga.ubuntuforums.org/showthread.php?p=10047142](http://www.uluga.ubuntuforums.org/showthread.php?p=10047142)

You need to be sure to install grub to the second drives MBR.

Some examples of installs:
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

See above for Maverick screens as they are somewhat different than Lucid was.
Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

I have the same issue (installing 'buntu on a second HDD) - I have found that a custom install is the preferred method (putting GRUB on the second drive) as opposed to chancing mucking with Windows' bootloader (in most cases, Windows does *not* like having its loader messed with).  I have two SATA drives (one with only Windows, and the other has only Maverick Meerkat) and by letting each have their own loader on their own drive, I can still have commonality of data (all on the Windows drive, for now).

---

