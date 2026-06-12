---
title: "Main issue is difference between USB Thumb destination and USB Disc dest"
date: 2016-10-03
forum: Installation &amp; Upgrades
---

### Post by informative on 2016-10-03
What I still struggle with (with many Linux flavors not just Ubuntu Lubuntu) is if I make the destination a USB Thumbdrive it works perfectly.  If instead I choose any form of DISK (be it 2.5" hdd or Solid State 2.5 disc) the Linux software is clever enough to know it is a disc and not a USB and then it assumes that regardless of it being a USB portable removable device that I certainly would plan to KEEP it attached forever and wants to place the bootloader on my devices main sda boot drive.  

Usually without giving any hints that it even plans to do so it will attempt to roofie whatever bootload you have setup on your main sda boot disk.  This renders your main boot disk hosed and your new portable install is worthless except when connected to it's new "home" PC.

I just want to be able to take a working USB and have the same thing on an SSD (with USB pigtail attached) so I can have more storage.  I've even tried using EaseUS and Acronis to replicate and stretch a working USB to an SSD and then it still lacks the needed bootloader MBR record or something and many efforts to get this added seem to fail me thus far.

Has anyone else here danced with this devil of an issue yet and discovered the fix?

---

### Post by informative on 2016-10-03
What irks me most perhaps is this same question posted to other forums like Backbox gets the typical "Oh (eyeroll) we haven't used 'Wincrapper' in years!  We wouldn't know about if it hosed someones Windows bootloader" which is a huge problem for the Linux community in my humble opinion.  So much contempt for Windows has crept in that people clearly don't care about the fact that (A) I didn't hose my windows bootloader (B) This has nothing to do with Windows (C) It is an issue which prevents migration of other users TO Linux (D) It makes the whole Linux community look really bad that they are fine with bad installs trying to crap on other peoples systems by doing unannounced "other drive" bootloader Grub roofie attacks.

---

### Post by yetimon_64 on 2016-10-03
When using the Ubuntu installer choose the "Something Else" option and manually partition, either with a pre-partitioned drive or by partitioning with the installer itself. 

There is a bar on the bottom of the partitioning page that allows you to set the drive for installing the bootloader to, by default it will have /dev/sda chosen. You can use the drop down arrow on the right hand side of the bar to choose which drive you want to install the bootloader to leaving /dev/sda untouched.

If you use the automatic install options I don't think you will even get to see the partitioner page of the installer, as a result /dev/sda is used by default ending up with the circumstances you write about in your post. 

Basically try the manual, "Something Else", option with the installer for your style of installations. I have installed many full ubuntu/linux systems to external drives (in a USB external dock system) without any trouble with the main bootloader on /dev/sda. Just be very careful to identify which is the proper drive to install to when selecting the bootloader option and all should work as you want it. 

Good luck and regards, yeti.

---

### Post by sudodus on 2016-10-04
+1

What ***yetimon_64*** writes is correct, when you install in BIOS mode. So if you can and want to install in BIOS mode, that is the way to do it :-)

-o-

But if you install in UEFI mode (standard in new computers), Ubuntu will automatically install the EFI system into the the first drive, /dev/sda, even if you tell it to install into another drive at 'Something else'.

There are work-arounds,

- Disconnect or unplug the internal drive(s) before you start installing. The you target drive will be the first drive, and it will receive all parts of the bootloader.

- Start from a compressed image of an installed system. I would recommend a mini-system with only text mode. After the installation you can easily install your favourite Ubuntu flavour or even make a custom system with your own choice of desktop environment and program packages. You can also install Ubuntu Server that way. See this link,

[Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

This will give you a portable system, that boots in UEFI as well as in BIOS mode (but it needs a 64-bit computer). And this method works, even with the internal drive connected.

-o-

There are other alternatives, other compressed images files, if you want to boot also in 32-bit computers (old computers). See these links,

[OBI/Xenial-32-txt](https://help.ubuntu.com/community/OBI/Xenial-32-txt)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](https://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by oldfred on 2016-10-04
The UEFI install only installs grub to drive seen as sda. But that does not modify the /EFI/Windows folder, so Windows can still be booted.

If wanting a UEFI bootable full install on a flash drive or any external drive you must gpt partition in advance with ESP - efi system partition. And then manually copy files from ESP on sda to external twice, once exactly and second time to have shimx64.efi in /EFI/Boot so you can rename it to bootx64.efi. 
UEFI only boots external drives from /EFI/Boot/bootx64.efi. Both Windows & Ubuntu installers use that file name, but obviously different files. And version of grub for installer is slimmed down version just configured for installer, where full install has just about everything.

This user posted more details. But may be copying too much to ESP?
Actual install is just any Something Else where you partitioned in advance.
Details on full UEFI install to flash drive or any external drive.
[https://ubuntuforums.org/showthread.php?t=2338836](https://ubuntuforums.org/showthread.php?t=2338836)

---

### Post by ubfan1 on 2016-10-04
This is bug 1173457, do consider adding yourself to the "Does this affect me" list.  The other "solution" is to make the ESP partition on the target USB, and after the install, just copy everything from the hard disk's ESP over to the the target -- the bootloaders are just files on a FAT filesystem.  Then make the "removable media" fix (the USB uses /EFI/Boot/bootx64.efi, so make that a copy of /EFI/ubuntu/shimx64.efi and also copy /EFI/ubuntu/grubx64.efi there.  A side benefit is that you now have a backup of the Windows bootloaders. ;^)

---

### Post by informative on 2016-10-05
What finally worked for me was the "something else" option but it was difficult to figure out what to build partition-wise.  I started with ext2 and a small swap like 8gb but it kept telling me there was no boot space.  finally I made a third partition of 200 MB which was FAT32 and told it to be mount just \ (backslash figured that is root?) still after I click next its targeting my sda instead of sdb So you have to watch the top row carefully and make sure only what you want is in that top row of partitions.  Also have to make it clear to click on the partition row below in addition to selecting the bootloader in the bottom dropdown selector.  This is way too complex for anyone even slightly green to computer stuff to navigate.  So happy I finally have my working USB SSD 120 gig portable Ubuntu working Thank you all for the good feedback.

---

### Post by sudodus on 2016-10-05
I'm glad it works for you :-)

If you feel that the problem is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

(If you feel that the method is too complex, I can understand that you might not feel like marking it as SOLVED, because the tag is there to guide other users, who are looking for a solution).

---

### Post by informative on 2016-10-05
I marked it as solved because it is solved for me.  I feel it is important to consider for the Linux Ubuntu community that we need to offer more "help" on that "Something Else" screen as far as tips and explanations.  20 years of IT work and I still struggled with how many manual partitions to make and what type ext2 ext4 swap what size and what "home\root" folders to apply and choose.  It is more than a little vague and ominous let's call it daunting.

---

### Post by sudodus on 2016-10-06
Is the information in the following link what you want?

[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by informative on 2016-10-08
Yes thank you - that helps.

---

