---
title: "Lenovo H430 Boot Error"
date: 2015-09-23
forum: Installation &amp; Upgrades
---

### Post by Mike_Rithjin on 2015-09-23
Please bear with me as I am not the most Linux literate. My goal is to have Ubuntu running on a Lenovo H430 desktop, which came with Windows 8 pre-installed (so I am told). I have tried all of the basic installs, erase total disk and reinstall, custom install on formatted partitions but I cannot even access GRUB. When I erase everything and try to reinstall I get the 'no operating system' error. Poking around the internet I think there might be some issue with getting my motherboard or BIOS or whatever hardware to point to GRUB, sounds like something Windows would do (lock down PC to make it difficult to remove Windows). I even tried to install windows, then Ubuntu on top and also alongside of it so see if windows boot loader would point to GRUB. I have tried various combinations of BIOS settings to no avail.

I tried to make some headway on some instructions I found in a different thread where you manually go into boot loader and change the .efi file but while I could find the Windows .efi file, I do not know where the grub or ubuntu boot file is that I can rename and place in boot partition. I might need to understand on a more fundamental level how GRUB works, but I have installed Ubuntu on many machines with absolutely no problem so this is really tarnishing my admiration for Ubuntu.

I really would appreciate some help with this problem.

---

### Post by oldfred on 2015-09-23
Have you installed in UEFI or BIOS/CSM/Legacy boot modes?
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

Best to see details.
Boot Ubuntu installer in UEFI mode and add Boot-Repair to it.

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Mike_Rithjin on 2015-09-23
Have you installed in UEFI or BIOS/CSM/Legacy boot modes?
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

-all i have done is put an install CD in the drive, clicked on the 'something else' option, selected my local ext4 partition and labled as '/' and then played around with various options in the 'install boot loader' drag menu at the bottom. I tried partitioning a new chunk as 'efi' partition and selecting it as the place to put the boot loader, all to no avail. I also played around in my BIOS testing all SATA options, and boot preferences.

Here is the boot-repair URL: [http://paste.ubuntu.com/12533398/](http://paste.ubuntu.com/12533398/)

thankyou for your help

---

### Post by Mike_Rithjin on 2015-09-23
Have you installed in UEFI or BIOS/CSM/Legacy boot modes?
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

-all i have done is put an install CD in the drive, clicked on the  'something else' option, selected my local ext4 partition and labled as  '/' and then played around with various options in the 'install boot  loader' drag menu at the bottom. I tried partitioning a new chunk as  'efi' partition and selecting it as the place to put the boot loader,  all to no avail. I also played around in my BIOS testing all SATA  options, and boot preferences.

Here is the boot-repair URL: [http://paste.ubuntu.com/12533398/](http://paste.ubuntu.com/12533398/)

thankyou for your help

---

### Post by oldfred on 2015-09-23
You installed in BIOS mode on a gpt partitioned drive. 
You show the bios_grub partition where where has its core.img which is required for BIOS boot.

With only Ubuntu installed, you will not get a grub menu, normally. Only after an abnormal shutdown.
With BIOS you should be able to hold shift key from UEFI/BIOS screen until menu appears. 
If you were in UEFI mode it would be escape key, often several times as you have to catch it just as UEFI ends, and grub just starts.

How you boot install media, DVD or flash drive either UEFI or BIOS is then how it installs. Installer works for both. And UEFI boot menu for flash drive should normally show two boot entries for installer. One clearly UEFI and the other just the label or name of flash drive.

It looks like it should just boot. Can you hold shift key to get to grub menu?

You show Ubuntu 14.04.2, but current live installer is 14.04.3, is it an older installer?

You have a very large bios_grub partition. Normally you have 1 or 2MB unformatted for it.
The ESP - efi system partition for UEFI boot is normally 100 to 500MB formatted FAT32 with boot flag.

You booted Boot-Repair in UEFI mode, which is ok. If you had an ESP partition, you could use Boot-Repair to convert to UEFI boot, but not required. Some systems make UEFI boot a bit more difficult to configure. But UEFI also has some advantages.

I actually create both the ESP & the bios_grub on all my drives including flash drives. But only one or the other is really required.
With very large TB sized drives like you have I prefer smaller system partition and larger data partition(s) or /home as separate partition.

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]10-25 GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

