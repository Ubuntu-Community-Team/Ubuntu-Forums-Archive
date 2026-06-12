---
title: "Installing Ubuntu on a Windows 7 PC"
date: 2010-11-28
forum: Installation &amp; Upgrades
---

### Post by Paragon009 on 2010-11-28
I'll admit. I'm lost. But, hey, can I at least get *some* credit for wanting to use Ubuntu? (Thank you)
 
So, I have a PC with Windows 7 x64 OS. The PC has a 750 GB HDD. I have been using this PC for about a year. The HDD is obviously defragmented since Windows 7 automatically defragments weekly.
 
I would now like to install Ubuntu on the PC's _only_ HDD while also maintaining the current Windows 7 x64 OS on the same HDD. Originally I was considering just buying another HDD to install Ubuntu on, but now I think it's easier to just install on the same HDD where Windows 7 installed.
 
I've searched and I can't seem to find one comprehensive thread on this forum (or an article from the internet) that explains how to install Ubuntu on a HDD that is _not_ pre-formatted/ wiped clean. Often, the articles suppose that the individual has a brand new or recently formatted HDD in which they want to install both Windows 7 and Ubuntu. But, I already have Windows 7 installed. Now I'd like to install Ubuntu in a partition.
 
I know it's probably best to use a clean HDD and install Windows 7 and Ubuntu from scratch (if you will), but I dread installing all my program drivers on a clean HDD. That's the main reason I'm not doing that type of install.
 
I do _not_ want to use Wubi.
I do _not_ want to use a USB.
 
Can I mount the ISO file to install Ubuntu so I don't have to actually burn it?
 
The most assistance I need is with partioning. Am I using Windows 7 or Ubuntu to do it? Am I supposed to partition the HDD before even installing Ubuntu?
 
Thank you in advance for your insight and the time you have taken to answer my questions. Your assistance is greatly appreciated.

---

### Post by dino99 on 2010-11-28
welcome in our world :)

first, shrink w7 partition(s) if needed, then:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

[https://help.ubuntu.com/community/Installation/FromUSBStick#Introduction](https://help.ubuntu.com/community/Installation/FromUSBStick#Introduction)

---

### Post by Enigmapond on 2010-11-28
Welcome...

Just follow the directions here [http://www.ubuntulinux.org/desktop/get-ubuntu/download](http://www.ubuntulinux.org/desktop/get-ubuntu/download) and everything will work out. It will automatically partition and format that partition. I installed off of a USB and all went well and no..if you want a true dual boot you need to boot up the USB and not mount the ISO. Good Luck.

---

### Post by GenePayne on 2010-11-28
This tutorial has some sections about installing on a HDD that already has an OS on it:
[HTML]http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml[/HTML]

It mentions the "use largest continuous free space" install option, and discusses the manual partition option. I found the installer to be quite good at showing you the partitions and details for each. I have successfully installed around the windows partition in the past. And yes, the installer can create partitions for you.

You will have to burn the .iso image to disc. You can't reboot with an .iso image mounted.

---

### Post by Paragon009 on 2010-11-28
I see many are using 10.04 rather than the newer version, 10.10. Why would this be? Is it just because the newer version may have unforeseen bugs/ glitches and some people are simply being cautious?

---

### Post by dino99 on 2010-11-28
> **Paragon009 said:**
> I see many are using 10.04 rather than the newer version, 10.10. Why would this be? Is it just because the newer version may have unforeseen bugs/ glitches and some people are simply being cautious?

its as in the real life :)

some are always on the bleedind hedge and others are always scared; by the way when bugs are fixed, they are first on the latest release.

---

### Post by Enigmapond on 2010-11-28
If it's you first time, I would stick with an LTS (Long-Term-Support). 10.04 IMO is the current most stable distro. I only install LTS's and have no problems. You can always try the others later on...there are a lot of bugs yet in 10.10 as you can see by all the posts in the forum.

---

### Post by matt_symes on 2010-11-28
Hi

> **Paragon009 said:**
> I see many are using 10.04 rather than the newer version, 10.10. Why would this be? Is it just because the newer version may have unforeseen bugs/ glitches and some people are simply being cautious?

Yes to both. Some people have had problems with 10.10. Also 10.04 is an LTS (long term support) version and the desktop version will be supported for 3 years.

BTW: Use the windows tools to shrink the windows partition.

Kind regards

---

### Post by Paragon009 on 2010-11-28
I love this community already. :P
 
What are the pros and cons of installing Ubuntu on a HDD with Windows 7 already installed (i.e., both OS on same HDD) versus installing Ubuntu on a second (new) HDD?
 
From what I understand, the former scenario seems to be easier. You shrink the partitions using the Windows 7 utility, install Ubuntu, and then, IIRC, you would get the Windows 7 boot allowing you to choose between Windows 7 or Ubuntu upon start-up.
 
The latter scenario involves disconnecting the SATA cables from the HDD during the installation process.
 
I guess my concern is having to uninstall Ubuntu. It seems to me that the latter scenario is preferable if it ever came to that because one could simply remove the second HDD and it would not complicate Windows 7 OS. But, it would be more difficult if Ubuntu was located on the same HDD as the Windows 7 OS, correct?
 
Once again, thank you for your great insights and efforts in answering my questions.

---

### Post by Enigmapond on 2010-11-28
I have installed many Ubuntu distros on many computers with one HDD and have never encountered problems. Because it's partitioned they really don't mess with each other and you could very easily delete either partition without it effecting the other. My guess is you will want to do that with Win7 as soon as you see that beautiful Ubuntu on your system...my suggestion is to not second guess yourself and just go ahead and do the easiest of the two choices...you will like it...

Good Luck!

BTW I have one HDD on my laptop with three partitions...one is the Win7 OS the second is NTFS formated just for storage and the other is ext4 for Lucid works out very well.

---

### Post by oldfred on 2010-11-28
I have 3 drives, so I am a fan of multiple drives. I have XP & 3 versions of Ubuntu, old , current & beta plus a few partitions for other / (root) in case I want to experiment across the 3 drives.

If you have an HP or Dell I would definitely recommend a separate drive. The have known software that corrupts grub in the MBR.  Also many win7 installs use all 4 primary partitions and you have to decide what to delete/copy to convert the last primary to the extended partition to hold all the logicals to install Ubuntu to. If you have a vendor system restore you should create those DVDs and if it lets you create a repair CD do that also.

Separate drive lets you keep win7 as a bootable standalone drive and grub in the new drive will let you boot both. The issue with the second drive is grub will default to installing to sda (usually your window) and overwrite the windows boot loader. That is fixable but it is easier to either partition in advance and use manual install so you can choose where to install grub or (to be absolutely sure) disconnect the windows drive when you install.

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)
[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

---

### Post by Paragon009 on 2010-11-28
> **oldfred said:**
> If you have an HP or Dell I would definitely recommend a separate drive. The have known software that corrupts grub in the MBR.
Hmm...interesting. I never heard that before. Yes, I do have an HP desktop and Dell laptop (though, it's the HP that is mine). I bought the HP for my wife, later reappropriated it for myself, and then modified some of the hardware. She now has the antiquated Dell. ;)
 
I'll read all those links. Thank you.
 
**Edit**: In this link, the author selected "erase and use the entire disk" when installing Ubuntu. Now, I know the HDD on which Windows 7 is installed has numerous partitions. Three or four, right? Is it necessary to partition the second HDD when installing Ubuntu, or does Ubuntu not need partitions like Windows 7 (e.g., for recovery, etc.)?

---

### Post by oldfred on 2010-11-28
The grub team was looking for users that have the issue with win7 software corrupting grub, so they could try to work around it. Most suggestions are just to stop using HP or Dell software that does not comply with industry standards.

Writes to MBR-----------------------------------
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
[http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable](http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable)
In Windows 7, I had to remove Windows 7 DataSafe.
HP ProtectTools, Dell Recovery, and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct or Uninstall Dell DataSafe issues with MBR
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

---

