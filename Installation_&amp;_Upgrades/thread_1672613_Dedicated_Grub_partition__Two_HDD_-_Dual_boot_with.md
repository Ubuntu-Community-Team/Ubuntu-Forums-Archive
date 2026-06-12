---
title: "Dedicated Grub partition : Two HDD - Dual boot with windows"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by snimavat on 2011-01-21
Okey.. Here's what I want to do.

I have two seperate HDD
HDD 1 : 160 GB (dedicated to windows, already working)
HDD 2 : 500 GB Will be using dedicated to ubuntu (not partitioned yet) 

I want to use the HDD two only for linux and this HDD is not partitioned yet. 

What I want to do is 
- A dedicated Grub partition (/boot) on HDD 2 (Do I really need it when I am using just two os? Will it work on second HDD?)
- / root partition
- /home partition
- /swap partition
- /fat32 partition (do i need it to share files with win?)

Can any one answer my questions and give a step by step guide to do it. 

Thanks
SN

---

### Post by presence1960 on 2011-01-21
You really do not need a separate /boot partition unless you have an older BIOS that cannot read past a certain point on the disk. But since you are using this disk exclusively for ubuntu you will not have that problem occur. Stay away from separate /boot partition unless absolutely necessary.

For sharing data between multiple OSs NTFS is better than FAT32.

To setup this install you will need to put the second disk (linux disk) as first in the hard disk boot order in BIOS. Boot the Live CD/USB and choose try ubuntu. When the desktop loads go System > Administration > Gparted Partition Editor. partition your linux disk. Create an ext4 partition for /, a linux-swap partition for swap and an NTFS partition for shared data. For swap it is recommended to make it as large as your installed RAM in case you want to hibernate.

When partitioning is complete use the install ubuntu icon on the desktop to begin installation. At the partitioning window choose manual install. Highlight the / (root) partition and click change. Choose file system under "use as", and under mount point choose / from the drop down box.
Proceed with the install. One note: at the window where you choose a user name do not use CAPS or spaces or you will not be able to proceed with the installation.

Keep the linux disk as first disk to boot in BIOS. The reason is you have GRUB on MBR of linux disk and the other disk has windows on MBR. If something should happen you can always boot to windows in an emergency by putting the disk with windows first in the boot order or depressing the boot device key at startup - my computer uses F9. Yours may use another key. Refer to your documentation.

---

### Post by psusi on 2011-01-21
You can have separate partitions for /boot and /home if you want, but there is little to no benefit in doing so ( unless you are booting multiple Linux installs ).  You also can create a fat32 partition if you want, or you can just mount your main Windows ntfs partition from Ubuntu, which can access it just fine.

---

### Post by thetractorking on 2011-01-21
Hi. I'm pretty new to Ubuntu, having tried it once last year. I think this thread may answer my question, but want to be sure (and hope I'm not posting this in the wrong place.) 
Just ordered a new custom built from Cyberpower, with a 30gb ssd as boot disk w/ windows 7, and a 1tb hd as data drive. would like to know if I can add another ssd w/ ubuntu, and be able to boot the machine from either one.

---

### Post by dino99 on 2011-01-21
> **thetractorking said:**
> Hi. I'm pretty new to Ubuntu, having tried it once last year. I think this thread may answer my question, but want to be sure (and hope I'm not posting this in the wrong place.) 
Just ordered a new custom built from Cyberpower, with a 30gb ssd as boot disk w/ windows 7, and a 1tb hd as data drive. would like to know if I can add another ssd w/ ubuntu, and be able to boot the machine from either one.

follow this little help:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by oldfred on 2011-01-21
I think presence1960 has covered most of the questions from the OP. Some links to installs that show the screens to make it easier to understand the process. Including two drives version from Herman.

Installs:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)

It does not have to be encrypted:
Standard full install to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

---

### Post by cascade9 on 2011-01-21
> **psusi said:**
> You can have separate partitions for /boot and /home if you want, but there is little to no benefit in doing so ( unless you are booting multiple Linux installs ).  You also can create a fat32 partition if you want, or you can just mount your main Windows ntfs partition from Ubuntu, which can access it just fine.

Having a seperate /boot might not give you any (real) benefits, but having /home does. It sure makes installing a different distro/reinstalling without having to back up everything easier.

---

### Post by psusi on 2011-01-21
> **cascade9 said:**
> Having a seperate /boot might not give you any (real) benefits, but having /home does. It sure makes installing a different distro/reinstalling without having to back up everything easier.

It doesn't matter for reinstalling ( just don't check the format box ).  I suppose if other distros don't give you that option, then switching would benefit from having a separate /home.

---

