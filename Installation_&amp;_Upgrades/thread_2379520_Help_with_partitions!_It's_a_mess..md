---
title: "Help with partitions! It's a mess."
date: 2017-12-06
forum: Installation &amp; Upgrades
---

### Post by gastikirs on 2017-12-06
Hi.

I'm having a bad time trying to install Ubuntu along with W10.

I have a SSD and a HDD.
W10 is located in the SSD.

I want to install Ubuntu in the 1TB HDD.
Sounds simple, but when I entered the disk setup during the installation of Ubuntu it came up with this mess:

[IMG]http://i67.tinypic.com/deageh.jpg[/IMG]
[IMG]http://i63.tinypic.com/2e3mss7.jpg[/IMG]

How can I safely install Ubuntu in the hard disk without touching any W10 file?
I also wanted to keep space for W10 to use the HDD. 

So lets say I'd like to assign 300GB to Ubuntu. So it will run and have all its information in the 1TB disk, and W10 will be in the SDD and for files it will use the HDD.

Thanks!

---

### Post by leunam12 on 2017-12-06
I don't see a mess, your ssd is being identified as sdb and your hdd as sda. The first thing that you have to do is boot your Ubuntu Installation in EFI mode, 
then you have to create a new GPT partition table on your HDD (sda), 
then create the partitions that you need for Ubuntu with the ext4 filesystem. If you want to install everything on the same partition, 
the mount point has to be "/". If you create two separate partitions for root and home respectively, then your root partition has to be mounted on "/" and home partition 
has to be mounted on "/home". Then create a swap partition, which is usually the same size as your ram if you want to hibernate, I only have 4GB of RAM  
with 8GB of RAM and I have never had any problems. The rest of the disk has to be formatted as NTFS for Windows to be able to see it. The GRUB has to be installed on sdb, I think. 

I don't dual-bot anymore, but when I used to I remember that I always had to run boot-repair after installation. Read the official instructions below very carefully.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2017-12-06
If you do not have a gpt partitioned drive with an ESP - efi system partition as first drive sda, grub will not install.
Drives are enumerated in SATA port order. So do you have SSD in SATA1 or higher and HDD in SATA0 or lower number than SSD? Best to have SSD in SATA0 port and use ports in order for additional drives.

At minimum you need ESP on drive seen as sda.

I do prefer to have an ESP (and bios_grub) on every hard drive. So drive could be converted to boot in either UEFI or BIOS boot mode without having to totally backup, repartition & reformat.

       MBR(for BIOS) or gpt(for UEFI) partitions:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

From UEFI boot menu, how you boot install media UEFI or BIOS is then how it installs.

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by gastikirs on 2017-12-06
Wow. I thought it would be easier. I dont understand a word of what you said lol.
Isnt there like an easy install? Or at least a tutorial for dumbs

---

### Post by leunam12 on 2017-12-06
The first thing that you have to do is get your motherboard user's guide and identify which SATA connector is SATA0 
and plug your SSD to that one, that way the installer will see it as sda, right now it sees it as sdb, the reason why 
this is important is because your boot loader has to be on drive sda. look at your second picture, see where it says 
"/dev/sdb1 efi", that partition is where the boot manager resides and it has to be on /dev/sda. so, your first step is plug 
your ssd on SATA0 or the lowest number.

---

### Post by oldfred on 2017-12-06
If you disconnect HDD, and use Windows to shrink the NTFS partition to make room for Ubuntu, then it should install without much issue.

But better to make sure HDD is gpt partitioned, just for future use.

---

### Post by gastikirs on 2017-12-06
Its a laptop. I cannot open it, what can I do?

---

### Post by leunam12 on 2017-12-06
> **oldfred said:**
> If you disconnect HDD, and use Windows to shrink the NTFS partition to make room for Ubuntu, then it should install without much issue.

But better to make sure HDD is gpt partitioned, just for future use.I believe the OP wants to install Ubuntu on the HDD.

---

### Post by oldfred on 2017-12-06
But Ubuntu's grub only installs to an ESP on drive seen as sda. If that is SSD then it will work just fine. But if HDD seen as sda or HD0 in UEFI/grub then grub will not install.

---

### Post by leunam12 on 2017-12-06
It is a laptop and it came with two hard drives? I find strange that the OS is installed on the secondary drive. can you swap them?

---

### Post by gastikirs on 2017-12-06
> **leunam12 said:**
> It is a laptop and it came with two hard drives? I find strange that the OS is installed on the secondary drive. can you swap them?

Yep, It came with the SSD 128GB (which is only for the OS i guess) and 1tb hdd.

BTW. I'm really noob and barely understand what you all are saying. I just wanted to install Linux and try a different OS but its been really complicated. Perhaps I wont do it, I dont wanna screw it lol

---

### Post by gastikirs on 2017-12-06
Ok, so I managed to install ubuntu. Shrinked the big HDD and installed it there. Also made the swap thing.

Thing is, I cannot choose between OS when boots. It just boots from the SSD. Any idea how to solve this?

---

### Post by oldfred on 2017-12-06
Did grub then install?
From UEFI can you choose ubuntu entry?

What brand/model system?

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by gastikirs on 2017-12-07
I'm sorry. I have no idea what grub or uefi is. What I did was schrinking the HDD. Then I had free space to work on. I did the swap thing, gave it some memory, and the rest for the OS. So Ubuntu was installed in the HDD.
The thing is that it boots always the windows in the SSD. is there any way I can choose between both OS when it boots?
Please try to be as simple as possible, I have zero experience in those things.

EDIT: followed these instructions and now its working! [https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)

---

