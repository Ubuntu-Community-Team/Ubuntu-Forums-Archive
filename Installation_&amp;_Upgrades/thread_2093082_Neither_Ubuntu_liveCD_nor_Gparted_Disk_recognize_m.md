---
title: "Neither Ubuntu liveCD nor Gparted Disk recognize my harddisk"
date: 2012-12-09
forum: Installation &amp; Upgrades
---

### Post by Jefferson1 on 2012-12-09
Hello,

after having [problems with wubi]("http://ubuntuforums.org/showthread.php?t=2092912") i wanted to install ubuntu using a liveCD. but the installation manager did't let me start the installation due to a lack of hdd space - but actually i'm having enough space. so i tried to make a new partition using a gparted but this says too that there is no hdd in my computer.
theres already a bootable windows 7 on my PC so the hdd works all fine.

**long story short: linux doesn't see my HDD, windows does.**

i already tried 'fdisk -l' in gpartedlive and ubuntulive; it shows nothing, not a single drive.

my system:
asus a8v-x motherboard
amd opteron 180 (2,20ghz dual core, 64bit)
ati radeon hd 4xxx (don't know exactly) graphicscard
HDD: samsung sp2504c (serial ata 3; 250gb)
1GB noname RAM

thanks in advance

---

### Post by Mister08 on 2012-12-09
> **Jefferson1 said:**
> Hello,

after having [problems with wubi]("http://ubuntuforums.org/showthread.php?t=2092912") i wanted to install ubuntu using a liveCD. but the installation manager did't let me start the installation due to a lack of hdd space - but actually i'm having enough space. so i tried to make a new partition using a gparted but this says too that there is no hdd in my computer.
theres already a bootable windows 7 on my PC so the hdd works all fine.

**long story short: linux doesn't see my HDD, windows does.**

i already tried 'fdisk -l' in gpartedlive and ubuntulive; it shows nothing, not a single drive.

my system:
asus a8v-x motherboard
amd opteron 180 (2,20ghz dual core, 64bit)
ati radeon hd 4xxx (don't know exactly) graphicscard
HDD: samsung sp2504c (serial ata 3; 250gb)
1GB noname RAM

thanks in advance

Can you see it in another distro? Puppy Linux, for example... If you can, it may be the fact the HDD is outdated and would need a driver in order to be mounted. 

Another possibility, is that the newer versions of Ubuntu may also not be compatible, the drive according to [http://openbenchmarking.org/s/SAMSUNG%20SP2504C](http://openbenchmarking.org/s/SAMSUNG%20SP2504C) it works on Ubuntu 11.04. Try using an older version

---

### Post by oldfred on 2012-12-10
Have you used all 4 primary partitions?

Post this from a terminal in liveCD

       sudo fdisk -lu /dev/sda
sudo parted /dev/sda unit s print

    
I hve nVidia, but understand older ATI need help.
       This repository provides AMD Catalyst drivers for legacy graphics Radeon HD 2xxx - 4xxx for Ubuntu 12.10 Quantal Quetzal.
[https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)

---

### Post by darkod on 2012-12-10
Sometimes there are errors or corruption in the partition table and linux can't display the partitions correctly, but windows can ignore these errors. However, this might be difficult to troubleshoot if no linux tools can see the disk.

Try again with fdisk and parted as oldfred suggested, and lets see if it can detect it.

Linux is usuallu very good at detecting hardware. Linux had sata drivers included and could install on sata disks even when XP still needed a floppy with drivers to see a sata disk. I remember that from years ago. If everything is OK with the disk, it's weird for linux not to detect it.

---

### Post by Jefferson1 on 2012-12-10
> **oldfred said:**
> Have you used all 4 primary partitions?

Post this from a terminal in liveCD

       sudo fdisk -lu /dev/sda
sudo parted /dev/sda unit s print

    
I hve nVidia, but understand older ATI need help.
       This repository provides AMD Catalyst drivers. for legacy graphics Radeon HD 2xxx - 4xxx for Ubuntu 12.10 Quantal Quetzal.
[https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)

the first command shows nothing, the second one tells me that there isn't such a device. 

I also tried puppy Linux with the same results as in ubuntu and gparted. 

please help me, I'm really desperate about this.

---

### Post by oldfred on 2012-12-10
Post screen shot from Windows partition tool. 

Most unusual that fdisk or parted do not show anything. That usually means BIOS does not even see drive.

---

### Post by Jefferson1 on 2012-12-10
my Windows recently stopped working but I don't think it has something to do with my Linux problem because the problem with Windows is new. because of this I can't show a screenshot but I slightly remember what my partition screen shows: one partition with about 60th left (250gb overall) and one with 800mb overall. that's the one Windows automatically creates at its installation. 

my bios sees my hdd..

---

### Post by darkod on 2012-12-10
It's not about the number of partitions. There are other things that Disk Management shows, like if disk is Basic or Dynamic, the partition layout in case there is some weird setup/corruption, etc.

One case where the installer doesn't show the disk is if there is raid meta data on it, if it was used in fakeraid earlier. But in that case Gparted from the live cd should show the disk and partitions, also parted should show it. So I don't think this is your problem.

But in any case, try this:
Boot the ubuntu cd in live mode and in terminal try:
```
sudo dmraid -ay
sudo parted -l
```

See if that output anything interesting.

Another option to repair basic partition problems is fixparts. You can run it even though right now we are not sure these are partitioning problems. There is a .deb file that you can download in live mode, install it, and then simply open the disk with:
sudo fixparts /dev/sda

Note that sda might not be recognized so this might only return some error like that.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by Jefferson1 on 2012-12-11
dmraid showed nothing and sudo parted -l shows: warning: unable to open /dev/sr0 read-write etc. 
sr0 seems to be my dvd-drive according to poppy. 
i couldnt use fixparts because it's installation results in a crash with the ubuntu live cd and with poppy linux i can't start it, it says: "cannot execute binary file"

a friend of mine told me it could be something with my bios and its sata settings, i already tried to randomly change settings that have to do with my hdd - with no results. 
is it possible that is has something to do with the fact that i encrypted one folder (just a folder, not the entire space or partition) with truecrypt?

---

### Post by darkod on 2012-12-11
Yes, that could have something to do. Even when it's only one folder, often encryption information goes on the MBR too, and can make the disk hidden. I guess for protection.

However, since I have no experience with truecrypt, I will let someone else give you advice on that.

---

### Post by Jefferson1 on 2012-12-11
SOLVED!

Someone had this problem earlier with the same mainboard as me (asus a8v-x):
[Sata problem on asus a8vx]("http://ubuntuforums.org/showthread.php?t=837835")

i had to add the 'pci=nomsi' bootoption  ([here is a howto]("https://help.ubuntu.com/community/BootOptions"))

and it worked! :D

thanks for the help

---

