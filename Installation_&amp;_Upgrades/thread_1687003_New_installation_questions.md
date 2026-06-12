---
title: "New installation questions"
date: 2011-02-13
forum: Installation &amp; Upgrades
---

### Post by TCMGO on 2011-02-13
I have chosen Ubuntu to install on a total computer rebuild (my XP system had a fatal crash so I am staring fresh). As I have very little experience in building computers, I have a few questions to start with:[
 
1. I downloaded Ubuntu 10.10. I take it that it will work on Intel or AMD processors (I am working with an Abit NS7-S V2 motherboard). Will I be able to upgrade to the next version of LTS or should I download Ubuntu 10.4 LTS and use it instead?
 
2. I want to set up a dual boot system (with Windows XP). Which is better . . . to install Ubuntu first or Windows XP. 
 
3. I am thinking to install both Operating systems on one 80Gb SATA drive and use another 640 Gb SATA drive for software applications and data (documents, etc.). Is 80GB enough space? Do I need to partition the 640 Gb drive to separate the Linux applications from the Windows?
 
4. How and when (before or after loading Linux and XP) do I go about upgrading the motherboard bios and drivers?

---

### Post by howefield on 2011-02-13
> **TCMGO said:**
> 1. I downloaded Ubuntu 10.10. I take it that it will work on Intel or AMD processors (I am working with an Abit NS7-S V2 motherboard). Will I be able to upgrade to the next version of LTS or should I download Ubuntu 10.4 LTS and use it instead?

Yes, your download will work on either Intel or AMD processors. Just don't download the 64 bit version if you are using a 32 bit processor.

Upgrading to the next LTS from 10.10 will mean upgrading each of the intermediate versions in turn, ie, 10.10 > 11.04 > 11.10 and so on up to 12.04. Whereas installing 10.04 means you can go straight to the next LTS. 
 
> 2. I want to set up a dual boot system (with Windows XP). Which is better . . . to install Ubuntu first or Windows XP.

Windows likes to think it is the only operating system on your machine and so will wipe out your Ubuntu boot loader, so install Windows first, then Ubuntu. 
 
> 3. I am thinking to install both Operating systems on one 80Gb SATA drive and use another 640 Gb SATA drive for software applications and data (documents, etc.). Is 80GB enough space? Do I need to partition the 640 Gb drive to separate the Linux applications from the Windows?

80 gig will house both operating systems with your data being held elsewhere, I find it easier to boot with the Live CD and use GParted to create the partitions before installing.
 
> 4. How and when (before or after loading Linux and XP) do I go about upgrading the motherboard bios and drivers?

I don't understand the question you are asking.

---

### Post by grahammechanical on 2011-02-13
I have never tried updating my motherboard BIOS program. It is scary! I do know that I need to download the new BIOS from the manufacturer's web site. I need to have an Operating system loaded to do that.

The motherboard manufacturer did supply a CD with Utilities, one of which can be used to download BIOS files and install them but these utilities are mostly Windows programs. I do not use them as I do not have Windows installed. There are some that will work from a floppy drive and are DOS.

I did build the machine myself and not purchase it. You can upgrade the BIOS after you have installed Operating Systems. The BIOS program is read before the operating system is loaded. Upgrading it should not affect the OS. I may be wrong. You should read the user guide that comes with the motherboard.

Regards.

---

### Post by cascade9 on 2011-02-13
> **TCMGO said:**
> 4. How and when (before or after loading Linux and XP) do I go about upgrading the motherboard bios and drivers?

I think you've got teh wrong model number, its more likely a NF7-S V2.0. If you really want to update the BIOS, you'llhave to go to the abit site, d/l awdflash (award flash) and the newBIOS. Load awdflash to one floppy disc, the new BIOS to another. The  restart, go into BIOS and make sure that you are set to boot from floppy. Restart again, put the awdflash floppy into the floppy drive, and then follow the instructions. 

Its probably not going to help anything, and I wouldnt be suprised if you already had the latest BIOS version. Its also got some risk, aside from user error. If there is power problem during the flashing process, yuo can be left with a dead motherboard..... 

*edit- if that doesnt scare you off upgrading the BIOS, its easier from XP. The BIOS updates are in .exe form (its basicly just a zipped file, but it needs to be run as a .exe to open. I dont know if WINE will open the BIOS .exe)  

As for drivers, they are all software, and ubuntu should look after them itself. Apart from the nvidia drivers anyway (and if you are using the onboard GF4MX IGP, you'll need to add a PPA or install the drivers manually)

---

### Post by oldfred on 2011-02-13
I also prefer to partition in advance. I also like to have a different operating system on every drive and its boot loader in the MBR of that drive. Then each drive can work without the other in case of drive issues. 

Too many links, lots of duplication:
Issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!
Installs:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)
Full Disk Install
[http://www.howtoforge.com/the-perfect-desktop-ubuntu-10.10-maverick-meerkat](http://www.howtoforge.com/the-perfect-desktop-ubuntu-10.10-maverick-meerkat)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate them from drive to drive.

Specific suggestions, but it may vary depending on how you want to use system. Even my own "best" configuration changes every couple of years.
For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.

---

