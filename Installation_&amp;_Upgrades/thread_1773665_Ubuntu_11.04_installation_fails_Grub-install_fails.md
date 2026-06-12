---
title: "Ubuntu 11.04 installation fails: Grub-install fails"
date: 2011-06-02
forum: Installation &amp; Upgrades
---

### Post by PearlChoco on 2011-06-02
First of all: I'm a complete Linux noob :)

My problem:
I'm trying to install Ubuntu 11.04 on a seperate USB hard drive (Samsung 120GB) using the Live-CD.
I tried multiple times but every time the installation hangs near the end (about 90-95%) and I get the following error msg:

[COLOR=#003D7D]"Executing 'grub-install /dev/sda' failed. This is a fatal error.[/COLOR]"

After that I can choose to continu without bootloader or to cancel the installation, but no matter what I select nothing happens.

Using Google I've found similar problems, but no proposed solution works for me.
This is what I tried:

- Standard installation, letting Ubuntu use the full hard drive.
- Manual installation, selecting a boot partition (500MB) and a root partition (rest of hard drive)
- Trying ext3 and ext4 file systems
- Using Ubuntu version 11.04 and 10.10 Live CD.

Always the same error.

One other thing: someone suggested using Ext2 filesystem. When I select Ext2 during installation, the installation hangs pretty much in the beginning during "creating Ext2 File system" (I've waited for 3+ hours and it doesn't move).
I tried to create an ext2 partition using GParted with the Live-CD (this works), and then selecting this partition during the installation, but again the installer hangs during "creating Ext2 File System".


Any advice how to procede? I really want to try Ubuntu!
Thanks!

My specs:

- Core i5 2500K
- Asus P8P67 Pro MB
- 8GB RAM
- Samsung External USB HD (all other HD's are disconnected)

---

### Post by Quackers on 2011-06-02
If you are installing to a USB hard drive then the bootloader would normally be installed to that hard drive as well - which would not normally be /dev/sda.
What is the drive designation of the drive you are installing Ubuntu on to?
To check that you can boot into the live cd/usb and select "try ubuntu" rather than "install ubuntu" then when the live desktop loads you can open gparted.
In the gparted screen it will display near top right a box with /dev/sda in it. I would suspect that this is your internal hard drive. Clcick on the small arrow next to that and in the drop-down box you will probably see another option, like /dev/sdb or /dev/sdc. 
Clcik on that option and you should hopefully see which is your USB hard drive.
If it is /dev/sdb then that's where you should be installing grub to.
This is done at the bottom of the partitioning screen during the installation.
There is a field entitled "device for bootloader installation" which is set by default to /dev/sda. If you click on the arrow next to that you should see a drop-down boix with other options in it (like /dev/sdb or /dev/sdc). Choose the one that matches with your USB hard drive, but take care not to use one with a number at the end - like /dev/sdb1, for instance. That is a partition. Grub should normally be installed to the drive, not a partition.

---

### Post by PearlChoco on 2011-06-02
Thanks for the reply.

Since I have disconnected all my internal hard disk drives (I don't want them to be "contaminated" with another OS's files), my only connected HD is the USB drive where Ubuntu should be installed.

GParted shows only one partiton (sda1).

[IMG]http://img833.imageshack.us/img833/1033/screenshotrhv.png[/IMG]

---

### Post by Quackers on 2011-06-02
Ok, thanks for that clarification.
I'm afraid I don't know whether ext2 is acceptable to Ubuntu 11.04. I suspect so, but I'm not certain.
In the first screenshot, did you change the field to "/dev/sda1" or did the installer do that?

---

### Post by PearlChoco on 2011-06-02
I've been trying ext2 with both Ubuntu 10.10 and 11.04.


I've made some screenshots during installation to clarify:
(Using ubuntu 10.10 - selecting ext3 file sytem)

[IMG]http://img691.imageshack.us/img691/3690/install1m.jpg[/IMG]
[IMG]http://img232.imageshack.us/img232/2025/install2v.jpg[/IMG]
[IMG]http://img33.imageshack.us/img33/7727/install3r.jpg[/IMG]
[IMG]http://img806.imageshack.us/img806/6026/install4.jpg[/IMG]
[IMG]http://img715.imageshack.us/img715/8716/error1l.jpg[/IMG]
[IMG]http://img51.imageshack.us/img51/9876/error2p.jpg[/IMG]

---

### Post by Quackers on 2011-06-02
You have an external drive that is a Samsung Mini and it's only 15GB in size - is that correct? I didn't know they made them that small :-)

---

### Post by PearlChoco on 2011-06-02
Hmm... that's weird, didn't notice that!

I'm very sure it's an 120GB disk.

Wait, this is the Disk Utility:

[IMG]http://img30.imageshack.us/img30/2252/disksd.jpg[/IMG]


Don't know what to think of this...

---

### Post by Quackers on 2011-06-02
Hmm, me neither  :-)
That is very odd.
The only thing I can suggest is to format the drive again (assuming you don't need anything that's on it) and then try again, noting its reported size.
Sorry I can't offer anything more insighful :-(

---

### Post by oldfred on 2011-06-02
I might try formating with gparted from the liveCD or USB that you are using for the install. See if that correctly sees the drive as 120GB.

I also would not use a /boot for a desktop system. Old systems, servers and those with RAID or LVM may need a /boot but most desktops do not.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by PearlChoco on 2011-06-02
Thanks for the replies.

I followed your advice and booted with Ubuntu 11.04 Live CD, and after formatting my USB drive I partitioned it using GParted (3 partitions: 15GB (root), 94+GB (home), 2GB (swap) ).

Then I launched the Ubuntu installer, and again it recognizes my Samsung S1 HD as a 15GB HD!
All 3 partitions are almost 10 times smaller than before:

[IMG]http://img703.imageshack.us/img703/3383/disks.jpg[/IMG]



Anyone knows what's going on here?
I tried the drive in Windows 7, and it behaves perfectly normal here.

---

### Post by oldfred on 2011-06-02
From LiveCD post this. But I expect it will match gparted not the installer:

sudo fdisk -lu

Post PT.txt
Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PT.txt

Have you checked that LiveCD is correct - mdsum? It also has a test as part of its menu.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by PearlChoco on 2011-06-04
> **oldfred said:**
> From LiveCD post this. But I expect it will match gparted not the installer:

sudo fdisk -lu

Post PT.txt
Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PT.txt

Have you checked that LiveCD is correct - mdsum? It also has a test as part of its menu.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)


Thanks.

```
sudo fdisk -lu

Note: sector size is 4096 (not 512)

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 1824 cylinders, total 29305206 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00048a76

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             256     3932415    15728640   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2         3932416    28786943    99418112   83  Linux
/dev/sda3        28786944    29305087     2072576   82  Linux swap / Solaris
```


PT.txt```


# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=      256, size=  3932160, Id=83
/dev/sda2 : start=  3932416, size= 24854528, Id=83
/dev/sda3 : start= 28786944, size=   518144, Id=82
/dev/sda4 : start=        0, size=        0, Id= 0
```

I've checked the Live CD 10.10 and 11.04 ISOs and they appear to be fine.

---

### Post by oldfred on 2011-06-04
I do not know the new 4K drives, but they can cause issues. I would expect the installer to see it correctly.

> Note: sector size is 4096 (not 512)First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of RAID arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)

Edit:
If it is only a 120GB drive why is it 4K partitions or is that the real problem that somehow that got changed? What are drive specs? Normally 4K is for very large drives 2TB and more.

---

### Post by geidorei on 2011-06-04
Hi

When I moved over to Ubuntu about three months ago I had similar issues, what I found out was that some USB hard drives, and sticks too, just arnt compatible with Linux. Abeit they will work as an external device one the OS is installed on another medium, they just wont accept an installation and certainly wont boot. 

I have a number of sticks, only of which 2 will boot, and 2 external hard drives where I tried to do the same and they too wouldnt accept an installation of Ubuntu. Newer externals Ive had no issues with, maybe its just older technology???

---

### Post by PearlChoco on 2011-06-08
> **oldfred said:**
> I do not know the new 4K drives, but they can cause issues. I would expect the installer to see it correctly.

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of RAID arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)

Edit:
If it is only a 120GB drive why is it 4K partitions or is that the real problem that somehow that got changed? What are drive specs? Normally 4K is for very large drives 2TB and more.

Thanks for the reply.

I can't find the exact specs of the drive.
Tom's Hardware reviewed it here ( [http://www.tomshardware.com/reviews/portable-storage-hdd,2272-4.html](http://www.tomshardware.com/reviews/portable-storage-hdd,2272-4.html) ) but can't find the specs.

Should I reformat the drive in some way?

---

### Post by pointym5 on 2011-06-30
I'm running into exactly the same problem, from the Alternate CD on a new HP dv6t laptop.  I'm not trying to dual-boot or anything; I'm reformatting the whole drive.

---

### Post by j4play on 2011-10-22
having same issue
kubuntu 11.10
single boot installation, but the pc does contain multiple drives. 
not having much luck today.

---

### Post by zghawking on 2011-10-31
First time trying to install Ubuntu here.

Used GParted to set up the partitions as extended 50gb partition:
sda5: 100mb boot logical partition ext2
sda6: 4gb swap logical partition linux-swap
sda7: 20gb root logical partition ext4
sda8: 25+gb home logical partition ext4

Windows has a 100MB partition at the very beginning of the drive and I have a windows7 partition of 80GB.

I tried aligning the partitions to both MB boundaries and Cylindar boundaries and got the same error both times

"Executing 'grub-install/dev/sda5' failed. This is a fatal error." *with whatever number I try.

The first time when I am in the installation proccess and I am choosing partitions it tells me there is data existing in these partitions (about 10mb in boot, 400-500mb in swap and home) so I chose to 'format' for each of them since I thought perhaps GParted hadn't formatted the data.  However the second time through I did not reformat them at this stage and had the same error.

I am trying to install the 64-bit ubuntu and have used unetbootin to install from a USB card.  I noticed in the first error report that it said cpu type was AMD64, could this be the problem?  I am an Intel CPU but I also heard the AMD64 cpu type is leftover in ubuntu from before Intel started making 64-bit processors.

---

### Post by zghawking on 2011-10-31
Uh oh, I tried to re-install Grub from the USB Ubuntu and now no boot record is found for Windows or Ubunutu :(

Also, if I try to boot from the Windows CD it is stuck on the blue screen & mouse: nothing loads up.  ::((

Ah okay I figured it out in GPart I had tried changing the flag 'boot' to the boot drive I made.  I changed it back to the 100MB Windows System managed drive and now windows boots normally

---

