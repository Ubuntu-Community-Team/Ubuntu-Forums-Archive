---
title: "Trouble installing on laptop with no CD drive"
date: 2016-11-30
forum: Installation &amp; Upgrades
---

### Post by horsebox2 on 2016-11-30
I got a new laptop (HP Envy Notebook) and for some bizarre reason, its got no CD drive. Its got Windows 10 on it, I gave it a try, but I've had enough, non stop problems (I'm a web developer/programmer, coming from Ubuntu to this...), ****** command line interface, and its also really slow (I got 8Gb RAM which is 4X what I had before) . I need  to get back on Ubuntu, so I shrank the partition to 50% to make room for Ubuntu.  I didn't have a USB key initially, so I tried installing it from a harddrive partition, I tried UNetBootIn and it added a new entry to the Windows boot loader (which is really helpful cuz I can get into the boot options easily), but it wouldn't mount at all when I selected it from the bootloader menu. I was gonna try EasyBCD but it said it doesn't work properly with EUFI boot mode. 

So I installed Ubuntu (ubuntu-16.04.1-desktop-amd64.iso) on a USB key, first tried it with rufus and then with a second program and I'm having this problem. The installer gets stuck at the first step, and heres what it says after it gets stuck:
[https://i.gyazo.com/b92544fef1cf6deb775b675868f8663a.jpg](https://i.gyazo.com/b92544fef1cf6deb775b675868f8663a.jpg)

I left it running for 5 hours and it didn't change.

Secondly, if I try to boot up live mode, it gives me an error, it says something about recursion and says it fixed it but requires a reboot, then it outputs all of this:
 
[https://i.gyazo.com/689a561e428d8e98e2412291598e0da4.jpg](https://i.gyazo.com/689a561e428d8e98e2412291598e0da4.jpg)

With rufus, it automatically booted Live mode, and I got the same error. 

Another weird issue is that it alerts me each time that it needs to unmount /cdrom before it can continue, and tells me to close any applications using it. Odd considering I don't have a CD drive. I let the installer disable EUFI secure boot mode for me. I confirmed that its disabled:
> 
PS C:\WINDOWS\system32> Confirm-SecureBootUEFI
False


 I enabled legacy support in BIOS. I'm stuck, I don't know what to do. VirtualBox isn't a good option cuz the host OS is so slow. Would maybe formatting the new partition into Ext4 beforehand help (assuming it won't need to format it itself then)? Any help here would be really appreciated, I've been at this for a long time now, and wasted God knows how many hours just setting up development tools on Windows (with Ubuntu, you run a simple command and it does everything for you).


EDIT: I tried starting up EasyBCD again, and this time it didn't gimme the warning about EUFI mode, but still the linux options are grayed out:[https://i.gyazo.com/f89814c25dacc8ad5f9e9b643794e7f1.png](https://i.gyazo.com/f89814c25dacc8ad5f9e9b643794e7f1.png)

---

### Post by ajgreeny on 2016-11-30
Please do not add large images inline in posts; some users are still on limited connections and will give up waiting before the post ever shows.  Either use a URL link as I have now done for you, or even better add images as attachments by taking screenshots, if possible, and using the paperclip icon in the text entry or Reply to Thread box.

To your problem; did you check the md5sum of the .iso image file you used?
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
Have you definitely disabled secure-boot, and fast-startup (or whatever that is now called)in the UEFI settings?  I am unaware of that ability being part of any installation procedure, but I admit I do not know refit if that is the utility that you are saying did it.
You must also make sure you boot the install medium in UEFI mode as that is how the new OS will be installed and as you have a new machine with Windows 10 pre-installed it will certainly be in UEFI mode.

Tell us the spec of the HP Envy Notebook in m,ore detail as it may help us come up with some ideas.

---

### Post by horsebox2 on 2016-12-01
_**UPDATE:**_ ajgreeny, I looked into quick start and it turns out I had it enabled. I switched it off, and will try the installation again later. According to the guide this person wrote (the first reply):
[http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook](http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook)
fast startup can cause complications with reading and writing to the MBR, that might explain why the installer couldn't install GRUB (as I mentioned below in my update). 

Sorry, I'll post links from now on. So this situation is really messed up. I found an option to boot up the USB drive in non UEFI mode:
[https://gyazo.com/5955a4fe1548b2ad5f5000b705c66f2e](https://gyazo.com/5955a4fe1548b2ad5f5000b705c66f2e)
and this enables me to get into Live mode (sometimes, 70% of the time it crashes along the way), and also get a whole lot further in the installation process. Its a different installation procetoo, because this time it tells me to setup an extra partition to store the GRUB bootloader. And when I create the new partition, I can set the partition type to BIOS Boot partition so thats what I did. So like this I have 3 new partitions, the SWAP partition, the Ext4 partition and the GRUB Boot partition. This time the installer got much further than it previously did:
[https://gyazo.com/2e7aedb4c3af4a4b9e5198fb8a231246](https://gyazo.com/2e7aedb4c3af4a4b9e5198fb8a231246)
you see there its about 60% done. The same errors appeared in the console, but it kept proceeding. All seemed well until this happens:
[https://gyazo.com/c5daf02c5e3d9464d8ecaf6a187be80c](https://gyazo.com/c5daf02c5e3d9464d8ecaf6a187be80c)
it tells me it couldn't install GRUB on the boot partition. It then gave me the option to continue with installation and would have to install GRUB later, thats fine by me, but right after I click continue, the installer crashes:
[https://gyazo.com/f0b0ddb87b8613edaa73d3a3082dc2ec](https://gyazo.com/f0b0ddb87b8613edaa73d3a3082dc2ec)

and thats it. Theres no way past that point. I've tried installing this way twice now, and it crashed in the same way both times. First the GRUB error, then it crashes. Now the installer detects the Ext4 partition as being a Ubuntu installation so its partially installed. But the GRUB thing, maybe I can install GRUB onto it myself from Live mode? I wanted to try that, but it crashed every time I tried to get into live mode. I got into Live mode once, but my 3 other attempts crashed. What the hell is going on here? On my old laptop, I never once experienced the installer crashing, never once had a problem getting into Live mode. I had a CD drive though and thats what I used. This is a nightmare because Windows is slowing me so much, I'm working at about 30% of my usual capacity. And right now I'm working on a critical project with a deadline. 

ajgreeny: Thanks for the reply, I'll get those specs now. To answer your questions first, secure boot is definitely disabled. I know that by running this command in PowerShell:
> PS C:\WINDOWS\system32> Confirm-SecureBootUEFI
which returns **False**. And I also saw it in the BIOS menu listed as disabled. The menu was grayed out so I had no option of enabling it again. I don't know what quick start up is. I haven't checked the md5sum of the .iso file, what will that tell me? Also I should mention that the program I used to install the bootable USB I'm using now is **LiLi**. 

Heres the specs:
[U][B]
SUMMARY:[/B][/U]
> OS Name    Microsoft Windows 10 Home
Version    10.0.14393 Build 14393
Other OS Description     Not Available
OS Manufacturer    Microsoft Corporation
System Name    LAPTOP-72BLDDCI
System Manufacturer    HP
System Model    HP ENVY Notebook
System Type    x64-based PC
System SKU    N7H25EA#ABU
Processor    AMD A10-8700P Radeon R6, 10 Compute Cores 4C+6G, 1800 Mhz, 2 Core(s), 4 Logical Processor(s)
BIOS Version/Date    Insyde F.13, 26/10/2015
SMBIOS Version    2.8
Embedded Controller Version    80.34
BIOS Mode    UEFI
BaseBoard Manufacturer    HP
BaseBoard Model    Not Available
BaseBoard Name    Base Board
Platform Role    Mobile
Secure Boot State    Off
PCR7 Configuration    Elevation Required to View
Windows Directory    C:\WINDOWS
System Directory    C:\WINDOWS\system32
Boot Device    \Device\HarddiskVolume1
Locale    Ireland
Hardware Abstraction Layer    Version = "10.0.14393.206"
Username    LAPTOP-72BLDDCI\horse
Time Zone    Eastern Standard Time
Installed Physical Memory (RAM)    8.00 GB
Total Physical Memory    7.47 GB
Available Physical Memory    3.52 GB
Total Virtual Memory    9.28 GB
Available Virtual Memory    3.56 GB
Page File Space    1.81 GB
Page File    C:\pagefile.sys
Hyper-V - VM Monitor Mode Extensions    Yes
Hyper-V - Second Level Address Translation Extensions    Yes
Hyper-V - Virtualisation Enabled in Firmware    Yes
Hyper-V - Data Execution Protection    Yes


and heres the Harddrive and also the USB key I'm trying to install from:

> Description    Disk drive
Manufacturer    (Standard disk drives)
_**Model    General USB Flash Disk USB Device**_
Bytes/Sector    512
Media Loaded    Yes
Media Type    Removable media
Partitions    4
SCSI Bus    0
SCSI Logical Unit    0
SCSI Port    0
SCSI Target ID    0
Sectors/Track    63
Size    7.55 GB (8,110,126,080 bytes)
Total Cylinders    986
Total Sectors    15,840,090
Total Tracks    251,430
Tracks/Cylinder    255
Partition    Disk #1, Partition #0
Partition Size    7.56 GB (8,114,929,664 bytes)
Partition Starting Offset    1,048,576 bytes
    
**_HARDRIVE:_**
Description    Disk drive
Manufacturer    (Standard disk drives)
Model    ST2000LM003 HN-M201RAD
Bytes/Sector    512
Media Loaded    Yes
Media Type    Fixed hard disk
Partitions    8
SCSI Bus    1
SCSI Logical Unit    0
SCSI Port    0
SCSI Target ID    0
Sectors/Track    63
Size    1.82 TB (2,000,396,321,280 bytes)
Total Cylinders    243,201
Total Sectors    3,907,024,065
Total Tracks    62,016,255
Tracks/Cylinder    255
Partition    Disk #0, Partition #0
Partition Size    260.00 MB (272,629,760 bytes)
Partition Starting Offset    1,048,576 bytes
Partition    Disk #0, Partition #1
Partition Size    937.68 GB (1,006,828,167,680 bytes)
Partition Starting Offset    290,455,552 bytes
Partition    Disk #0, Partition #2
Partition Size    29.30 GB (31,457,280,000 bytes)
Partition Starting Offset    1,007,119,499,264 bytes
Partition    Disk #0, Partition #3
Partition Size    8.38 GB (8,999,927,808 bytes)
Partition Starting Offset    1,955,354,116,096 bytes
Partition    Disk #0, Partition #4
Partition Size    838.19 GB (900,000,000,000 bytes)
Partition Starting Offset    1,055,353,995,264 bytes
Partition    Disk #0, Partition #5
Partition Size    819.00 MB (858,783,744 bytes)
Partition Starting Offset    1,984,652,378,112 bytes
Partition    Disk #0, Partition #6
Partition Size    13.86 GB (14,882,439,168 bytes)
Partition Starting Offset    1,985,511,161,856 bytes
Partition    Disk #0, Partition #7
Partition Size    18.90 GB (20,298,334,208 bytes)
Partition Starting Offset    1,964,354,043,904 bytes


---

### Post by ajgreeny on 2016-12-02
I have just noticed that this is an HP machine.

HP like to make life difficult for we Linux users by making changes to the UEFI firmware that is contrary to the standards that were supposed to be used by all.  HP have changes these so that the only UEFI boot files that can be used are named Windows.

I have not personally come across this and my desktop and my wife's laptop, both using UEFI were dead simple to manage with an install od Xubuntu, neither of them dual booted either so much easier to deal with.

Have a look at [https://ubuntuforums.org/showthread.php?t=2147295](https://ubuntuforums.org/showthread.php?t=2147295) from which I quote:-
> It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)I hope this helps a bit more.

---

### Post by ubfan1 on 2016-12-02
If you ISO fails the hashcheck, it is garbled, and unlikely to work, producing a variety of strange, random problems.  Redownload the ISO rather than trying to fix it, although maybe a zsync of the bad ISO might actually fix it (rehash to check).
Doing the below can save you a lot of time struggling with a bad install media or hardware problems:

1) md5sum check the downloaded iso.
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.
  For other releases' hashes, like lubuntu, see:
  [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
2) If using a CD/DVD,  burn the disc as slowly as possible.
  See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
3) Select the media check before trying to install.
 [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
4) Do a "memory check" (perhaps another live-media menu choice) on your PC.

---

### Post by horsebox2 on 2016-12-13
After I switched off Windows Quick Start, I was able to install GRUB on the GRUB partition, and was able to fully install Ubuntu. When I tried to boot up Ubuntu it crashed though. Heres the error it gives when I try to boot into Ubuntu:
[https://gyazo.com/c0faad14d44fc7df8a70da6da17198d5](https://gyazo.com/c0faad14d44fc7df8a70da6da17198d5)
and heres the menu that appears in the boot manager:
[https://gyazo.com/865ce3809ae7f3acd830cc1440b77fce](https://gyazo.com/865ce3809ae7f3acd830cc1440b77fce)

The GRUB menu appears when I go into the UEFI Ubuntu option, but it crashes no matter what I select, Ubuntu, Ubuntu Safe Mode, the same thing happens, it won't boot into Ubuntu at all. I tried a new ISO file, but it didn't help. The main reason I switched to Ubuntu in the beginning is because Windows is the embodiment of capitalism and parasitism. Linux is the embodiment of socialism/altruism/egalitarianism and symbiosis. This is pretty dark stuff. A laptop with no CD drive, which locks you into UEFI mode...

---

### Post by horsebox2 on 2016-12-26
I'm still stuck on this issue, its locked me into Windows which is a big problem, because it means I need to learn everything twice, how to do things on Windows and how to do them on Linux. Also, if something happened where Windows gets corrupted and I'm locked out, then I have no way to boot up a live Linux distro to fix it. Has anyone here successfully installed a dual boot system on one of these EUFI computers?

---

### Post by ubfan1 on 2016-12-26
You need to reread ajgreeny's links, partitcularly [http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889) #6 oldfred's HP suggestions.  HP decided to boot only things named "Windows Boot Manager", and you are still trying to boot the name "ubuntu".  Yes, you will have two "Windows Boot Managers" after the rename, but blame HP, not the UEFI standard.

---

