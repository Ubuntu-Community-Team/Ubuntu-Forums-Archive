---
title: "Unable To Use PC Partitions Upon First Installation"
date: 2016-12-07
forum: Installation &amp; Upgrades
---

### Post by hangman13us on 2016-12-07
Hey guys,

got an available laptop to setup HP-EliteBook 840 G1. I'm using my Kubuntu w/o any issues and etc. Not too advanced user but manage all I need via the embedded interface of Ubuntu. I've decided I'm going to run this laptop with Grub to load Win7 Prof. and Linux Ubuntu 16.04 LTS. So far so good. I've installed my Windows, made the partitions leaving 100GB - Win / 75 GB Linux and ~300GB for storage. Windows started fine, I've formatted the partitions under Windows as NTFS, named them and etc.

Next step - I started with 64Bit Version of Ubuntu, downloaded the latest LTS version and made bootable USB Stick. However when I start the installation Ubuntu runs O.K. I went trough the main changes (I haven't used Ubutu for a while, but Kubuntu is almost the same apart of the appearance), when I start the actual installation though I've been shocked I don't have HDD listed (see screen 1). It gives an error I'm unable to understand (suspect it was something related to the HDD Properties and how I installed the Windows on a first place - I'm running on SATA - AHCI - see screens 2&3)

Surprisingly enough (screen 4) I'm seeing the partitions just fine through the Partition Manager under Ubuntu. I also see them when I run my Windows... When I tried to find more about this issue I've run across few documented cases where people explain it depends on how you've installed your Windows... and for some reason Windows wipe out some of the drivers as unnecessary for it... which can cause such issue. I'm absolutely fine to start from scratch (re-imaging my Windows and my Ubuntu) but would appreciate if someone can explain to me what I did wrong and how to get this fixed next time? Also do you know what could be the primary cause for this problem and can I sort it out now w/o installing everything again?

[IMG]http://imgur.com/mH6HIcE[/IMG]

[IMG]http://imgur.com/9Usa22I[/IMG]

[IMG]http://imgur.com/C99cM7K[/IMG]

[IMG]http://imgur.com/dzBBJPJ[/IMG]

Appreciate your responses and support on this,
hangman13us

---

### Post by yancek on 2016-12-07
Your GParted output shows all of the space on the entire drive taken up by windows (ntfs) partitions except for 1.02MB of unallocated space.  There is no where to install Ubuntu.  You need to boot into windows and shrink one of the partitions to leave unallocated space on which to install Ubuntu then format it during the install.  After resizing the partition in windows, you should run chkdsk from windows until you show no errors.  It is not possible to install and have a functioning Linux system on a windows filesystem any more than it would be possible to install a windows system on a Linux filesystem.  It just won't work.

---

### Post by hangman13us on 2016-12-07
Thank you Yancek,

If I understood correctly - then a simple re-imaging of my Win7 so I leave a part of the HDD unallocated should work just fine. I wonder if I can do something simialr with partition manager under Windows and try to save time installing windows again. Will think it through and will post progress if I manage to sort this out w/o further help.

Appreciate your response! :)

---

### Post by oldfred on 2016-12-07
You show sda2 as NTFS but labeled Linux. 
While Linux can read & write NTFS, it only installs to Linux formatted partitions. Default type is now ext4.
But Linux likes to have a swap partition in addition.
And better to have the extended partition as last partition with all the logical partitions inside it.

If no data yet in sda3, may be easier to delete & recreate. There are tools to convert partitions to logical if they can be inside the extended following several partition rules.

With the BIOS/MBR configuration you can only have 4 primary partitions and one of those can be the extended partition which then acts as a container for all the logical partitions.

Do not use Windows to create more partitions. If it offers to convert to dynamic, do not let it. It is a one way conversion and does not work with Linux. Dynamic also does not work with all Windows tools.

---

### Post by hangman13us on 2016-12-07
Hm, I'm stuck again...

I've deleted the partition 2 which was NTFS indeed but it was just a label to help me with the installation when I have to use it. Then I made the following:

/Dev/SDA1 - 100GB NTFS (supposed to be my Win7 Partition)
/Dev/SDA3 - 70GB EXT4 (Meant to be my Linux Ubuntu Partition - I've used **GParted Partition Editor** to create it)
/Dev/SDA4 - 5GB Swap (Initially I wanted to create this during the installation, as I've always did it this way, but now I created it manually with GParted)
/Dev/SDA2 - 300GB (meant to be a storage area shared by both OS' - the Win and the Linux.

However my issue is when I start installation it does not point me to any available partition I can use. SDA3 is not visible even formatted now as EXT4, Swap is not visible and etc... I recall in the past I used to see the entire HDD - It used to say - here is your Windows, here is your storage space here is some un-allocated and etc. I don't mind putting the big X on all of this and start from scratch - the laptop is a blank page at the moment so I don't have issue with this. But I'm unable to get Ubuntu installing anywhere at all... which is really odd, and that's why I think it has something to do with the BIOS or the HDD configurations.

PS: firstly I tried installing the distribution w/o formatting the partition - it was simply erased and listed as un-allocated in the GParted. Results - same as above.

Now I shall go through the topic olfred shared to see if I can get any idea what was wrong with it...

thanks,
hangman13us

---

### Post by oldfred on 2016-12-07
Your sda1 NTFS partition may need chkdsk. After any resize NTFS needs chkdsk. And then the Linux NTFS driver will not mount it.
Is Windows installed & booting ok from sda1?

---

### Post by hangman13us on 2016-12-08
Hi Oldfred,

Yes Windows load just fine. I've been told to use F6 during booting and use "nodmraid", but my ubuntu image doesn't give me chance to use advanced options menu. I tried with Windows 8.1 few hrs ago, but Linux failed to recognize the partitions again. I removed the entire HDD structure and partitions - left it unassigned so I don't make linux file system on top of previously used FAT/NTFS, but no results. Now I'm re-creating my usb stick with other version of Ubuntu I've downloaded from the site with the idea I try to use "nodmraid". Let's see if it will work.

PS: I ran scans and checks of the HDD few times yesterday - just in case, didn't help much. However I've noticed there is a SSD (30ish GB). When I was going through the materials in the web there was someone with similar problem using Dell PC ([https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1062625](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1062625)) but I'm not sure he managed to sort this out.

regards,
Hangaman13us

---

### Post by soumyas.sarkar on 2016-12-08
You have a Linux partition as NTFS type. Any reason why. Refer image 4.jpeg?

---

### Post by hangman13us on 2016-12-08
Hi Soumyas,

It was only in the start as I installed Wind7 first. I've allocated the disk for Windows and put 2 additional partitions in NTFS - one that was supposed to operate with Ubuntu and one for storage area. The idea was to re-format it in EXT4 when I install the Ubuntu. It didn't recognize it properly. So later I formatted it as EXT4 + SWAP, then as "unallocated" space... and still nothing.

I've been told to use nodmraid from advanced options upon install but for me it is available only on previous version of Ubuntu. Even when I tried it - doesn't work. I'm actually out of any actual clue where the problem might be. I've also tried Kubuntu distribution - same. It doesn't recognize the HDD and I cannot proceed with the installation. :(

---

### Post by hangman13us on 2016-12-08
I wonder could it be something related "anti-thief" features of the HDDs recently? Encryption or something. Since the first failure to install I read so many things I literally lost myself somewhere in the middle of all versions.

---

### Post by hangman13us on 2016-12-08
[IMG]https://s15.postimg.org/4glnj00rf/Screenshot_from_2016_12_08_10_56_04.png [/IMG]

See here for instance. I just made these changes again. And again it doesn't show them in the installation menu - it is empty as if I don't have HDD at all. :(

---

### Post by hangman13us on 2016-12-08
Can someone more experience help me read these two:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1058415](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1058415) (I believe this is my issue)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1057690](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1057690) (I believe this is the fix) but I'm not sure how do I apply this, do I run Ubuntu and install this package when I'm using the live boot? And then the partitions are supposed to work? It says the fix is available, but I don't have a clue how to apply it.

thanks in advance,
hangman13us

---

### Post by oldfred on 2016-12-08
Both of those are old bugs.
First is if RAID was ever on drive, the desktop installer will not work. Drive keeps RAID meta-data even if RAID is turned off. We also found that some laptops with Intel SRT have same issue.

Second is LVM related. Gparted does not work with LVM - logical partition management. But installer should be able to. With LVM you have to use LVM tools to partition inside the physical partitions. Gparted only works on physical partitions.

You do not have LVM, but drive could have RAID meta-data on it if drive was ever part of a RAID or if you had turned on RAID or Intel SRT in UEFI/BIOS.

One of the other issues we see is Windows users who use Windows to create more than the 4 MBR allowed primary partitions. Windows works with extended and logical, but often converts to a proprietary dynamic partition system which is similar to Linux' LVM. Recently noticed that newest Ubuntu does now see dynamic partitions, it used to not work at all.
Are partitions shown as basic in Windows?

       Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
Even if raid not used BIOS may have set parameters, Also check BIOS settings should be AHCI
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings

---

### Post by hangman13us on 2016-12-08
Thank you, it actually worked. I can see the partitions in the installation manager now. It gave me some warning the removal of RAID could lead to problems with the other OS. I start playing with them and consequently none of the OS' worked fine. Ubuntu didn't load after the restart, and the windows was totally messed up - asked me for CD to repair it "due to latest hw changes".

Anyway, the step has been made. Now I'm running few checks and scans. Will repeat as many times as I need to so I get it the way I want it to be. Will post the final result, but wouldn't be able to do this w/o the help I saw here.

Thank you.

---

### Post by oldfred on 2016-12-08
I really did not expect that to be the issue, it was a last gasp.

---

### Post by hangman13us on 2016-12-09
I thought seeing the partitions will sort things out, but not... What happened is something beyond my comprehension. When I saw them (partitions) I started the installation despite the warning I may not be able to boot my windows. 

[[img]https://s28.postimg.org/n12cbh5e1/20161209_102446.jpg[/img]](https://postimg.org/image/n12cbh5e1/)

I actually just wanted to make a test to see if Ubuntu would work normally on this PC. I tried ubuntu only, I tried using the small SSD as I suspected this was this problem. but the result wasn't even close to independent ubuntu running on this laptop. If I install it alongside windows it fails to load any OS but shows my windows and ask for repair disk. I formatted the entire HDD and even "sanitized" it overwriting previous data system partitions or legacy OS'. No result. If I install ubuntu only it doesn't load and gives me an error the grub failed to install a pack:

[[img]https://s28.postimg.org/4wzbqu7pl/20161209_101102.jpg[/img]](https://postimg.org/image/4wzbqu7pl/)

and when I restart it fails to complete the restart with such non-sense (to me) lines:

[[img]https://s28.postimg.org/qm2t8fzbd/20161209_114930.jpg[/img]](https://postimg.org/image/qm2t8fzbd/)

After applying the lines oldfred gave:
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

I can at least see the HDD and the partitions. To be on the safe side I let ubuntu do everything alone (to use full disk drive) or even to use the SSD alone (it is 32 GB so must be enough to run on it...) but no results as I said. I need to admit I used twice "nodmraid" within advanced options of installation but it appears only if the HDD is fully blank from any data or previous OS. Today I'm already thinking I'm not suitable for linux and should give up.

---

### Post by oldfred on 2016-12-09
You have a newer UEFI system, but Windows must have been installed in the 35 year old BIOS/MBR configuration. 
When you booted installer you should have two choices if UEFI Secure Boot is off. One is UEFI:flash drive and the other is flash drive which is the BIOS boot option.
You have to install in same boot mode as Windows is installed as Windows in BIOS must have MBR partitioning and Windows must have gpt partitioning with UEFI. Ubuntu also uses gpt with UEFI.

Post this:
sudo parted -l

---

### Post by hangman13us on 2016-12-10
Fred,

The command [sudo pated -l] returned this: 

> ubuntu@ubuntu:~$ sudo parted -l 
Model: ATA HGST HTS725050A7 (scsi) 
Disk /dev/sda: 500GB 
Sector size (logical/physical): 512B/4096B 
Partition Table: msdos 
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags 
 1      1049kB  53.7GB  53.7GB  primary 


Model: ATA LITEONIT LSS-32L (scsi) 
Disk /dev/sdb: 32.0GB 
Sector size (logical/physical): 512B/512B 
Partition Table: msdos 
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags 
 1      1049kB  106MB   105MB   primary  ntfs         boot 
 2      106MB   32.0GB  31.9GB  primary  ntfs 


Model: hp v250w (scsi) 
Disk /dev/sdc: 4049MB 
Sector size (logical/physical): 512B/512B 
Partition Table: msdos 
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags 
 1      1049kB  4049MB  4048MB  primary  fat32        boot, lba 


ubuntu@ubuntu:~$ 

However when I proceeded the installation after the command I saw the installation type allowed me the option "install Ubuntu alongside Win7" which I don't recall previously during the process. It gave me the same warning for BIOS compatibility mode and that I may not be able to boot the other OS, but I decided to check what will happen:

[[img]https://s5.postimg.org/tkdaac2w3/Screenshot_from_2016_12_10_12_16_23.png[/img]](https://postimg.org/image/tkdaac2w3/)

The partition manager of the installation showed the Win7 loader as part of the /dev/sdb which didn't feel right, and the /dev/sda1 visible but obviously couldn't give details for used part of the partition.

Maybe the Windows installation doesn't go as smooth as it should? I don't know why ti uses the SSD instead the primary HDD. 

After the install - I see again these errors where it is unable to read parts of the disk (my previous post) and here we go again... Edit: this is not true: *messed up windows and not even a trace from the Ubuntu installation...*

Edit: I posted before I see the final results. This time (using the option to install ubuntu automatically alongside Windows 7) Windows loads fine, but there is no track from the Ubuntu installation. Seems like the grub doesn't work properly. Windows Partition manager says 50GB Windows partitions (healthy, active, primary) and 407GB (healthy, primary), and 7.9 GB (healthy, primary). However they, of course, are unaccessible and there was no Grub to let me load from the second partition.

---

### Post by oldfred on 2016-12-10
It looks like you erased sda.
Was Windows really only on sdb?

Many laptops with the small SSD used it only for a boot cache for Windows to speed boot. Windows boots so slow they made mfg add SSD to make it seem it boots faster. Often the software used was Intel SRT which was seen as RAID and need that removed.

But if an older Windows 7 system,  it may have been BIOS/MBR even though hardware was newer and UEFI capable. 
But then you have to either reinstall Windows in UEFI and install Ubuntu in UEFI mode. Or install Ubuntu in BIOS mode.
For both Windows & Ubuntu how you boot install installer UEFI or BIOS, is then how it installs.

With any system always safest to only use Something Else, and partition with gparted in advance. The auto installer works for standard systems, but the more complicated configurations or if Windows hibernated, or SRT or other special configurations & then it may not see the NTFS partitions and just erase entire drive.

---

### Post by hangman13us on 2016-12-11
Windows uses 50GB from the main drive (SDA). I'm not sure why I cannot install Ubuntu only (I tried this as well) it says the other system may not be able to boot, but when I completely remove the partitions in the main drive I suspect the SSD mess the things up and the computer thinks there is broken windows and asks to repair.

I don't know how to install both into BIOS or into UEFI - it isn't something I can actually chose from within the installation itself. Windows automatically uses the SSD (as you mentioned). Partially my problem is I couldn't make the ubuntu even work independently. It looks great with the live boot, but after the restart - doesn't load at all.

Do you have any solution where I can remove all from the two drives and try the machine with Ubuntu only? Last time (somewhere within my posts above) I even tried to use the SSD as primary for Ubuntu. It is big enough for it to operate properly and the entire drive of 500GB to be used to storage and etc. but it gave me broken windows again.

EDIT: PS. of course my main intention was to use Windows7 and Ubuntu 16.04 simultaneously. and I think my Windows is old by genuine so I used this old distro as a base to upgrade instead of buying brand new Windows. I have also windows 10, but I honestly think it sucks (pardon my French). :D

---

### Post by oldfred on 2016-12-11
You control UEFI install or BIOS install, by how you choose to boot install media for both Windows & Ubuntu. Windows 7 DVD is BIOS only, but can be copied to flash drive and a few files moved around to make it UEFI bootable.

My systems do not have UEFI Secure boot setting in UEFI. But call it "Windows" or "Other". But fine print says use "Other" for Windows 7 as it is not UEFI Secure boot capable.

You should have settings for UEFI or BIOS. Some just have one setting to switch, others have multiple settings in UEFI/BIOS to get it correct.
How you boot system once installed must match the mode you install in. You can boot installer in UEFI and install in UEFI, but have system set for BIOS. Or vice-versa.

Have you changed drive setting(s) to AHCI, should not be RAID, nor IDE. Not sure about the Intel SRT settings, but those may need to be off.

What brand/model system?

These are now older installs but had the Intel SRT.
              
 ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204) 
           
 Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

---

### Post by hangman13us on 2016-12-11
All good questions, but I can answer only few of them... :(

1) When I login in my BIOS (restart -> ext -> F10 -> Advanced -> SATA Device Mode = ACHI) This is one of the first things I checked. I think it was RAID and I wanted to "sanitise" the  disk and it didn't let me do it unless I change device settings.

2) When I boot from my USB I have few options
    a) External USB Hard Drive (I usually use this one)
    b) Boot from EFI File (this one actually leads me to the USB itself, but I'm lost there... I tried to go to / -> boot -> grub but then I don't have any options to load anything)
    c) M.2 SSD Drive (must be my windows as it uses it all the time)
    d) Notebook HDD
    e) USB Hard drive 1 - HP v250w (between this and point "a)" I'm not sure what to chose, I thought they are same as I have only this USB)
    f) Notebook Ethernet (never used it) 

I'm not sure between these 2 USB options which one is UEFI and which one is BIOS? If I have to repeat this again and chose only one of the options I'd love to do it but so far I got the impression I'm using the first one all the time.

With regards of Model / Brand /System - i'm not sure what you mean. The Laptop is:

HP EliteBook G1 840 ([link]("http://h71016.www7.hp.com/dstore/html/pdfs/AMS_HP_EliteBook_840_G1_Notebook_PC_Data_Sheet.pdf"))

Ubuntu is the latest available desktop distro - 16.04 LTS (x64)

My windows is Windows7, Professional (x64)

I'm really confused with these UEFI, BIOS, EFI, RAID and etc. stuff as they seem to be invisible, nobody anywhere asks me if I would like to use option 1, 2, 3... (n)
 
:(

---

### Post by oldfred on 2016-12-11
You may or may not have UEFI. Since it says one option was Windows 8, it probably is UEFI.
But then how you boot installer is how it installs.
In UEFI boot menu for flash drive should be two entries, one UEFI:flash and other flash  which is the BIOS option. Flash will be name, brand or label on flash drive.

You can tell how you have booted. You get black screen with tiny accessibility icons at bottom for just a few seconds with BIOS or black screen with grub menu.
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

You probably had Intel SRT which looks like RAID, you may need to turn of Intel SRT settings also. And perhaps USB settings on how you boot.

      
 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

Several users have just erased & removed RAID data from SSD and used it for / (root) for Ubuntu. You lose the faster boot of Windows, but SSD makes Ubuntu much faster. You then can have /home and/or data partition(s) on HDD for your data. I normally use 25GB for / on a SSD, but have all data on HDD.
At least once user noticed the Intel SRT cache was only using the amount of RAM on SSD, so he was able to also install / in the unused space on SSD.

These are now older installs, but newer Ubuntu should be similar. Then Intel SRT seems to be the same across all brands.

 ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
HP Envy  Windows 7 with MBR & SRT
[http://askubuntu.com/questions/159645/dual-boot-installation-of-ubuntu-12-04-lts-on-hp-ultrabook-envy-4-1002tx](http://askubuntu.com/questions/159645/dual-boot-installation-of-ubuntu-12-04-lts-on-hp-ultrabook-envy-4-1002tx)
Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)

---

### Post by hangman13us on 2016-12-14
Thank you OldFred,

I was reading the materials Inter SRT was a problem. I've managed to get the Ubuntu to work, and honestly - I'm fine for now. What I think is to explore 16 a bit more and so far it seems really improved since the last version I've use (it has been a while I used GNOME for last time).

The best for me is I think to keep it as it is for now. Will keep the topic in my own "home library" with IT related issues and will try to figure it out later.

I appreciate your help on this.

will mark this as "solved" and will point to: [https://ubuntuforums.org/showthread.php?t=2020155](https://ubuntuforums.org/showthread.php?t=2020155) as resolution to this issues, sometimes I guess the software version and etc may vary and cause variations of the problem but at least I have a brief idea what I need to go trough to get them both booting on a single PC.

Regards,
hangman13us

---

