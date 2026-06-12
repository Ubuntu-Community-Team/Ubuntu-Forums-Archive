---
title: "[KUBUNTU 20.04 LTS] Stuck in dual-boot installation hell on my Dell Vostro 14 3468."
date: 2020-05-13
forum: Installation &amp; Upgrades
---

### Post by atta-asmi-01 on 2020-05-13
Hi,
[SIZE=1][I]A bit of context: I'm fairly new to Ubuntu. I've been running KUBUNTU on a secondary laptop for ~6 months after my Software Engineering Professor instructed us to try to switch over to Linux. I took to KUBUNTU because of UBUNTU and the KDE personalization options (sucker for MacOS theme :p). Anyways, a week ago, that laptop broke (basically irreparable). 
[/I][/SIZE]
I decided to dual boot it on my primary laptop, Dell Vostro 14 3468 (Intel i7-7500U CPU @ 2.70GHz; UEFI; 8GB RAM; GPT Partition Table). I tried to install KUBUNTU, it failed (unable to install grub). Over the course of last week, I've tried to install Manjaro KDE, KDE Ne[SIZE=2]on, V[/SIZE]anilla Ubuntu and Kubuntu. **ALL FAIL AT THE SAME STEP**. Installer fails to install GRUB. All Data is copied successfully, as I can see it there when I boot live. have tried to manually install Grub ```
sudo update-grub
```, it slaps me with a 'read/write /dev/sda error'. At this stage, I'm just totally burnt out. I've tried all installation guides out there, to no avail.  Manually setting EFI partition; Guided Install alongside (resize partition) all fail.  

I'm able to run it Live from my USB. I know the iso files are A-Ok as I've checked MD5 sum, and it is currently running in VBox. With my finals approaching, I'm just stressed to the maximum. 

Right now, I'm just so overrun with information that it feels impossible to sum it all down here.  I'll edit and add any thing I remember frequently here. **_Ask me anything you guys need to know and I'll reply ASAP._** Please do keep in mind that I'm in GMT +5, so sometimes it might take upto 8-10 hrs for me to reply.

Hoping to get this sorted out. :)

Edit1: FastBoot and SecureBoot are Off. Have tried to both make /boot/efi part manually and let the installer make it manually. All Fails.

Okay, so update 2:
Again, the installation failed.
[ATTACH=CONFIG]285856[/ATTACH]

I deleted the previous partitions (swap and /) and had 30 GB of  unallocated space on my disk. I created a bootable USB using Rufus (in  ISO mode) and booted into it. On the Kubuntu splash screen, the  integrity check (?) completed without any errors. I know I booted into  UEFI mode as it showed the black screen, grub menu and not the  purple-ish screen. The installer had copied over all the files,  downloaded all additional software and language packs. I had even set my  account name and password. It was stuck on "Detecting Hardware, 66%",  when it showed the error.
[ATTACH=CONFIG]285855[/ATTACH]

Right now, I'm booted into the live USB. running ubuntu-bug ubiquity shows this.
[ATTACH=CONFIG]285854[/ATTACH]

All my partitions show up. even the Linux one. Boot folder does have a efi folder.
[ATTACH=CONFIG]285853[/ATTACH]

Right now, I'll keep the laptop booted into Live mode overnight. Any tests you want me to run, do let me know, 

If this helps: [BootRepairSysLog]("https://paste.ubuntu.com/p/dPkcF7mrPB/")

---

### Post by CelticWarrior on 2020-05-13
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

This should be your starting point to understand UEFI and how to install Ubuntu in UEFI mode, standalone or dual/multi-boot.
Also, if dual-booting with any Windows 8 or newer you must disable its Fast Startup feature. Honestly, that should be all.

---

### Post by atta-asmi-01 on 2020-05-13
FastBoot and SecureBoot are Off. Have tried to both make /boot/efi part manually and let the installer make it manually. All Fails.

> Note that in a UEFI-mode installation, Ubuntu will not ask you where to install the boot loader.
This seems interesting. I boot into UEFI mode, and when on the partition section, there is a little dialog box in the lower-left side of installer, asking me to do so.

---

### Post by CelticWarrior on 2020-05-13
So, you said you want to dual-boot... That means you already have another OS installed and running, right?
If that other OS is Windows and because you mentioned GPT it must have been installed in UEFI mode (all preinstalled Windows since 2012 certainly are), right? So there's an EFI partition there already. The only possible reasons for a Ubuntu UEFI automated installation failing at that stage would be an 'unclean' EFI partition due to Fast Startup in Windows (very rare but happens) or not enough space (very unlikely because any preinstalled Windows makes a ~100MB EFI which is more than enough for a second set of bootloaders). Now, if using the "something else" option (manual partitioning) users must select the existent EFI partition (as such) and at least the root partition (it used to be that and a swap partition but not currently needed since Ubuntu now uses a swapfile by default).

---

### Post by atta-asmi-01 on 2020-05-13
Okay, so do I only need to make a ~30GB ext4 partition to mount at **/** ,and no swap partition? And Should I guide the installer to the EFI partition Windows made? It is at /dev/sda3. Do I let the installer install bootloader at /dev/sda (which is default) or point it towards /dev/sda3 ?

---

### Post by yancek on 2020-05-13
30GB should be enough for the filesystem partition and Ubuntu will create a swap file during the installation so no need to create a swap partition. The installer will also use the EFI partition currently being used by windows.  It will create a separate directory there named ubuntu so it will not affect windows.  And yes, /dev/sda is what you select and it should install to the EFI partition.

---

### Post by CelticWarrior on 2020-05-13
But, again, if using "something else" you need to *explicitly *select the existing EFI partition as such.

---

### Post by atta-asmi-01 on 2020-05-13
Okay, Here goes try number 18 (I think).

---

### Post by ubfan1 on 2020-05-13
You should have tried grub-install from the live media, not update-grub -- all that (tries) does is rewrite the grub.cfg file on the live media, fails every time of course.

---

### Post by atta-asmi-01 on 2020-05-13
okay.

---

### Post by VMC on 2020-05-13
Actually Kubuntu doesn't need any help with the efi partition. It will figure that out. Lubuntu complaints if you don't select /boot/efi on efi.
Give us a printout of ```
lsblk -f
```, so we know what we're dealing with.

---

### Post by atta-asmi-01 on 2020-05-13
Okay, so update 2:
Again, the installation failed.
[ATTACH=CONFIG]285856[/ATTACH]

I deleted the previous partitions (swap and /) and had 30 GB of unallocated space on my disk. I created a bootable USB using Rufus (in ISO mode) and booted into it. On the Kubuntu splash screen, the integrity check (?) completed without any errors. I know I booted into UEFI mode as it showed the black screen, grub menu and not the purple-ish screen. The installer had copied over all the files, downloaded all additional software and language packs. I had even set my account name and password. It was stuck on "Detecting Hardware, 66%", when it showed the error.
[ATTACH=CONFIG]285855[/ATTACH]

Right now, I'm booted into the live USB. running ubuntu-bug ubiquity shows this.
[ATTACH=CONFIG]285854[/ATTACH]

All my partitions show up. even the Linux one. Boot folder does have a efi folder.
[ATTACH=CONFIG]285853[/ATTACH]

Right now, I'll keep the laptop booted into Live mode overnight. Any tests you want me to run, do let me know, 

If this helps: [BootRepairSysLog]("https://paste.ubuntu.com/p/dPkcF7mrPB/")

---

### Post by atta-asmi-01 on 2020-05-13
> **VMC said:**
> Actually Kubuntu doesn't need any help with the efi partition. It will figure that out. Lubuntu complaints if you don't select /boot/efi on efi.
Give us a printout of ```
lsblk -f
```, so we know what we're dealing with.

[IMG]https://i.imgur.com/nXhVWPV.png[/IMG]

---

### Post by VMC on 2020-05-13
I don't see /boot/efi. Don't post pictures, but instead copy paste between "codes". Your mountpoint is cut off, we need to see that.

---

### Post by atta-asmi-01 on 2020-05-14
Boot Info Summary
[https://paste.ubuntu.com/p/dPkcF7mrPB/](https://paste.ubuntu.com/p/dPkcF7mrPB/)

**lsblk -f result.**


```
NAME   FSTYPE LABEL       UUID                                 FSAVAIL FSUSE% MOUNTPOINT
loop0  squash                                                        0   100% /rofs
sda                                                                           
&#9500;&#9472;sda1                                                                        
&#9500;&#9472;sda2                                                                        
&#9500;&#9472;sda3 vfat               9C87-8880                                59M    39% /mnt/boot-
&#9500;&#9472;sda4 ntfs               E2A8F19BA8F16E83                       27.2G    73% /mnt/boot-
&#9500;&#9472;sda5 ntfs   Data        01D37BD9D975C4D0                       32.2G    81% /mnt/boot-
&#9500;&#9472;sda6 ntfs   Data II     01D37F5C14116740                       26.5G    82% /mnt/boot-
&#9500;&#9472;sda7 ntfs   WINRETOOLS  A84E0D4F4E0D1828                      437.8M     3% /mnt/boot-
&#9500;&#9472;sda8 ntfs   Image       3CAC0E20AC0DD4F4                      149.2M    98% /mnt/boot-
&#9500;&#9472;sda9 ntfs               722883F42883B59F                        621M    43% /mnt/boot-
&#9492;&#9472;sda10
       ext4               cac492c9-03e4-4d8b-b92a-5fcbfb8cf0f1   21.1G    23% /target
sdb                                                                           
&#9492;&#9472;sdb1 vfat   KUBUNTU 20_ D69C-1D29                              12.8G    15% /cdrom
```

---

### Post by VMC on 2020-05-14
Here's mine:```
NAME        FSTYPE LABEL    UUID                                 FSAVAIL FSUSE% MOUNTPOINT
sda                                                                             
&#9492;&#9472;sda1      ntfs   500GSSD  41B523622A4A8924                                    
sdb         vfat   SECURITY B6F9-A81C                                           
sr0                                                                             
nvme0n1                                                                         
&#9500;&#9472;nvme0n1p1 vfat            06F2-A932                              59.7M    38% /boot/efi
&#9500;&#9472;nvme0n1p2 ntfs   Windows  303E9A203E99DEE2                                    
&#9500;&#9472;nvme0n1p3 swap            f4ccc655-f7ba-44b5-b636-88a3cfd42b81                [SWAP]
&#9500;&#9472;nvme0n1p4 ext4   neon     357795a8-a2f9-4f52-bb52-beeff2b1f1c3                
&#9500;&#9472;nvme0n1p5 ext4   budgie   0defc081-b813-4565-a64d-0bb8b257038a                
&#9492;&#9472;nvme0n1p6 ext4   xubuntu  ae1bb60b-0428-47ed-bc28-2f64bb54fe9f   41.1G     9% /
```As you can see, my vfat shows "/boot/efi", yours doesn't.

---

### Post by atta-asmi-01 on 2020-05-14
So what should be the next course of action? I've had to exit the live instance and go into Windows for work. I just popped over to Disk Management and it shows that the 30 GB, ext4 partition is 100% free. but in the live instance, Dolphin showed it having data (the necessary linux folders).

---

### Post by oldfred on 2020-05-14
You will not correctly see Linux partitions from Windows. 

Are you booting installer in UEFI boot mode?
Is drive in UEFI settings, set to AHCI? Dell defaults to RAID or Intel RST and must be changed. But Windows needs the AHCI driver installed first or Windows will not boot.

Most Dell also need UEFI update and if SSD, SSD firmware update.

Some UEFI has settings that lock ESP or Windows bitlocker may lock ESP, so grub cannot install. Check UEFI and turn off bitlocker if using it.

A few need either Windows chkdsk or dos fsck on the ESP. Examples, use your ESP - efi system partition:
sudo fsck.vfat -t -a /dev/sda1
man dosfsck
sudo fsck.vfat -t -a /dev/nvme0n1p1

---

### Post by atta-asmi-01 on 2020-05-14
Yes, I'm booting installer to UEFI mode. In BIOS, boot mode is set to UEFI and the installer boots to the UEFI Grub screen (the black one with the last option being "*UEFI Firmware Settings*"). 

Drive is set to AHCI. I do have an Intel RST application that came preinstalled and it installs itself even if tried to uninstall. After checking in UEFI, Drive is det to AHCI. Can't find any option regarding Bitlocker.

My laptop only has an HDD. So should I only run the first two commands i.e. 
[I][B][COLOR=#000000]sudo fsck.vfat -t -a /dev/sda3[/COLOR]
[COLOR=#000000]man dosfsck
[/COLOR][/B][/I]
And should I run these in a Live Instance? Because I can't boot into ubuntu.

---

### Post by oldfred on 2020-05-14
As long as USB drive is still seen as sda.
My USB flash drives as sdb, sdc or whatever often become sda on reboot or if directly booted. Sometimes I have to change depending on whether I have directly booted or rebooted flash drive.

---

### Post by atta-asmi-01 on 2020-05-14
> **oldfred said:**
> As long as USB drive is still seen as sda.
My USB flash drives as sdb, sdc or whatever often become sda on reboot or if directly booted. Sometimes I have to change depending on whether I have directly booted or rebooted flash drive.

I'm sorry, but this reply makes no sense to me. 

/dev/sda is my HDD. USB is at /dev/sdb.

-----------------------------------------------------------------------------------------------

I plugged in my USB and started a LIVE instance. On All my previous instances, I had been unable to get Boot Repair to run. On this try however, it installed and ran. In the end it gave me the error. 
> Locked-ESP detected. You may want to retry after creating a  /boot/efi partition (FAT32, 100MB~250MB, start of the disk, boot    flag). This can be performed via tools such as gParted. Then select    this partition via the [Separate /boot/efi partition:] option of [Boot    Repair].

So, I guess /dev/sda3 is locked. But I couldn't find any setting  regarding to it in UEFI. Cannot create a /boot/efi partition from the  KDE Partition Editor (built in) as it doesn't allow mount points. What  to do next? Can't I just create another partition in the start of the  HDD (I do have ~522MB unallocated space there) and let Ubuntu boot from  there?

---

### Post by ubfan1 on 2020-05-14
You can create a mount point at /tmp/efi to mount sda3, and then run the file system checks on it.   sda3 is just a FAT filesystem, so it should be visible and fixable from Windows too.

---

### Post by oldfred on 2020-05-14
Either UEFI or Windows is locking it.
It may not mention ESP, but just security on boot or something similar. Or Windows turned fast startup/hibernation back on.

Really old bug, with some possible work arounds.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829)

Are you able to mount the ESP yourself?
Or mount read only?

---

### Post by atta-asmi-01 on 2020-05-15
Oh Lord! I just tried to boot to Kubuntu Live and it wouldn't identify the 30 GB partition. Now while running installer, it says that the /dev/sda is read only. 

At this point, I' ve just given up. I think Windows/UEFI is doing something to my HDD that freaks out the installation. Anyways, I've asked my friend to lend me his external Hdd so that I can backup necessary files, delete all partitions, install Kubuntu first, and then install Windows. That'll take a week or so. I'll mark this thread as answered. 

**THANKS TO ALL TO CHIMED IN AND HELPED. **:)

---

### Post by oldfred on 2020-05-15
I still suggest to install Windows first. But I do not have Windows. :)
But if not gaming, many here suggest installing Windows in a virtual install.

---

### Post by atta-asmi-01 on 2020-05-17
Acknowledged. :KS

---

