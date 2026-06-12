---
title: "HELP! Problems with Ubuntu 16.04 64-bit"
date: 2016-07-03
forum: Installation &amp; Upgrades
---

### Post by sinisterise on 2016-07-03
I'm ultra new to Linux.

CPU Info
- Core2Duo E7400
- 4GB RAM
- GPU GeForce 9800GT
-System supports 64-Bit
(Checked using uname -a)


Ok let me start off with the USBs used.

USB 1
-Sandisk Cruzer 4GB
-Supported File Systems : NTFS, FAT, FAT32, exFat


USB 2
-Sandisk Cruzer Switch 16GB
-Supported File Systems : NTFS, FAT32, exFat


I DO NOT have an optical drive(what ever you call that insert cd/dvd thingy)

BIOS/CMOS : 
-Intel I945 for BIOS
-Award Software 1984-2008
(OLD i guess)
Bios settings are done to proper instructions for installing(boot list, etc.) Legacy enabled as well.

Now the situations and problems.

Problem : Cannot Install Ubuntu x64

Device Used : USB 1
I tried creating a live bootable USB using Unetbootin, Works when the file system is FAT, but refuses to boot when the file system is FAT32. I tried using Unetbootin to create a bootable USB for installation of Ubuntu 16.04 x64. When i used file system FAT32, again it doesn't read at all(goes straight to boot my HDD). When i used file system FAT, it reads but it gets stuck at "Verifying system DMI pool data". I did this process more than once, redownloading the ISO, using different program like UUI. All had the same results as mentioned.


Device Used : USB 2
Same process, downloaded the ISO, used UUI to create a bootable disk. When i used file system FAT32, it doesn't read hence booting the HDD instead. Because this USB cannot be formatted to file system FAT, i tried using NTFS. On NTFS, Ubuntu 16.04 32-Bit was installed successfully into my HDD.(My HDD is now running Ubuntu 16.04 x32 OS) When i tried doing the same but this time using the x64 ISO, On NTFS, it reads but gets stuck at "unable to mount root fs on unknown block site: (2,0)".

I've come to the conclusion that my CPU cannot read/understand FAT32 system files. The reason I want to install x64 is because i am a crazy DOTA 2 player and DOTA 2 only supports 64-Bit Linux. I hope that someone can end my misery.(spent 5 days trying to install these while putting lots and lots of effort searching for solutions only to find a different problem) i can't afford a Windows OS as i am truely in financial difficulty.

MAIN QUESTION : How do i install Ubuntu 16.04 x64 without using a cd/dvd or FAT32 bootable disk? If i can't, is there any other solutions to play DOTA 2 on Linux(Other Distros)? 

I love Linux and would certainly hope someone can help me out. Thanks in advance.

---

### Post by ubfan1 on 2016-07-03
1) Did you md5sum check the downloaded iso?
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.
2) Did you select the media check before trying to install?
 [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
3) Did you ever do a "memory check" (perhaps another live-media menu choice) on your PC?
Doing the above can save you a lot of time struggling with a bad install media.

Now, times have changed, and the Ubuntu 16.04 ISO cannot be used on a FAT filesytem.  It contains a link necessary to set up the preseed area, and links are not allowed on FAT filesystems.  The current way which works is to use dd to copy the ISO to the USB.  Now dd itself is unforgiving of user mistakes like indicating the main disk is the target, so use mkusb to provide some safety net.  Take a look at the link [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by sinisterise on 2016-07-04
You my friend, ubfan1, i cannot possibly thank you enough for the dd suggestion. Finally, i have a 64-Bit Os running. Thank you my friend. May god bless you!


For those looking for information :

1. Checks done and matches everytime.

2. I couldn't do a media check as it resulted to the same results which was "unable to mount bla..bla..bla"

3. Memory check went smooth as ever. 

Solution to my issue(foolproof):

-Format a USB to NTFS file system.(Only if your system is as old as mine and it cannot read FAT32 system files)
On my laptop, i used win32diskimager. Write the ISO into my USB and BOOM! it worked.

---

