---
title: "Questions About Installing Ubuntu With Windows 7"
date: 2015-08-16
forum: Installation &amp; Upgrades
---

### Post by scottinpa40 on 2015-08-16
Hello, I decided to install Ubuntu 14.04.3 along with Windows 7 64-bit, which I just recently installed on a new Seagate 2 TB internal hard drive.  I tried Ubuntu Gnome first and had problems installing it - it would tell me to remove the installation media and restart the computer but it just booted into Windows, each time I tried, so I gave up on that.  Does anyone know why that would happen or have any thoughts on the Gnome OS?
My other question is how can I install the regular Ubuntu 14.04.3 to dual boot with Windows?  I already made a 32 GB partition on my hard drive and I have 2 other partitions...C, which has Windows OS on it and D, which has my data on it.  Is there an easy way to install Ubuntu on the separate 32 GB partition or do I need to install it in the C Windows partition to dual boot?  I have the ISO for Ubuntu on a DVD and wanted to install it with it unless using a USB flash drive is better.  I appreciate any help you can give me!  Thanks.

---

### Post by yancek on 2015-08-16
>  do I need to install it in the C Windows partition to dual boot

If you do that you will overwrite windows files and be unable to use it.

>  restart the computer but it just booted into Windows,

That generally means the bootloader was not installed properly.  A default windows system is not capable of booting Linux.  You could install EasyBCD on windows to boot it and Ubuntu but it is usually simpler to accept the default of Device for bootloader installation which is generally sda.  That would mean installing the Ubuntu Grub boot code to the master boot record of the first drive.  Did you remember to format the partition you created for Ubuntu with a Linux filesystem?  Windows can't do that.

Using a flash drive instead of a DVD won't make any difference.  Which option did you choose for the bootloader installation?  Which Installation Type option did you choose?

---

### Post by scottinpa40 on 2015-08-17
Thanks for getting back to me, I was trying to do the installation with the "Something Else" option and it was confusing to me, as I'm new to Linux.  It seems like it would be much more simple to use the "Install alongside Windows 7" but when I tried that, the slider would only let me go over to the right so far and the drive space for Ubuntu was almost 100 GB.  I thought it would let me shrink the size more but it won't.  I have 1.7 TB of free space on the D (Data) partition and that is showing on the page.  I have plenty of free space so if I have to accept the Ubuntu installation size as 100 GB, would that allow me to dual boot?  Thanks for your help and if it would be easiest to just do the install alongside Windows 7 with the slider, I will do that.  I'm guessing that it is just more of an automatic install for people like me that don't know much about Linux yet.  LOL  If I choose this option, will Ubuntu be on a separate partition than the D?  I definitely won't ever try to install Ubuntu on the C partition since that will overwrite Windows!  Thanks again for your help, I appreciate it.

---

### Post by yancek on 2015-08-17
>   I have 1.7 TB of free space on the D (Data) partition a

That won't help.  Free space inside a partition such as the data partition for windows is not the same as unallocated space and if you try to install Ubuntu there you will have nothing but problems.  You need to have unallocated space outside any partition on whcih to install.  If you have unallocated space the Install Alongside option should work, most of the time it does but, you are right about it being an auto type install.  You won't know what is happening until the install completes so it's more like cross your fingers and hope for the best.  It does usually work though.

To post more details on what your partitions actually show, boot the Ubuntu install medium and open a terminal and enter this command:  sudo fdisk -l(Lower Case Letter L in the command) and post the output which is a results.txt file.  That will give more information and someone should be able to help.

---

### Post by scottinpa40 on 2015-08-17
OK, thanks for the info.  So if I go to Disk Management on Windows, I should just leave unallocated space there instead of making a new partition?  Right now I have (C) Windows, (D) Data and there is a System Reserved space which I know not to mess with.

---

### Post by Quarkrad on 2015-08-18
Can you post a picture of your Disk Management window?  If we can see this picture it will help guide you through what to do.  I (like many others) have exactly what you want - i.e. dual boot win7 an Ubuntu.

---

### Post by Bucky Ball on 2015-08-18
*Thread moved to **Installation & Upgrades**.*

Yep, I have a Win7 dual-boot also.

Boot to the BIOS, switch off secureboot, continue with the boot to the USB, install, choose Something Else, create / as 30Gb and /swap as 2Gb (you mention something about having a 32Gb partition). Mark the EFI partition (which will be FAT32 and you will see it clearly) to 'Use' but _make sure it is unticked for format_. You **don't** want to format it. Leave any NTFS partitions you see there. Don't touch 'em and don't mark to use and especially not format.

Continue with the install. Any luck?

The thing is, Win7, if pre-installed, will (probably) be in EFI mode. Please confirm. If so, you need to make sure you are installing Ubuntu in EFI and not legacy. Good luck and let us know.

For a closer look you can post your boot info.

BootInfoScript download:
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Instructions:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by scottinpa40 on 2015-08-19
I attached a picture of my Disk Management on Windows. thanks for your help!

(The picture is in my next reply, I forgot to attach it)

---

### Post by scottinpa40 on 2015-08-19
Sorry, here's the attached picture...

---

### Post by scottinpa40 on 2015-08-19
Bucky Ball, I have a question...is secure boot the same as quick boot in BIOS?  I checked my BIOS and only found the quick boot option.  As far as the 32 GB partition, I opened that up to install Ubuntu on, through Disk Management in Windows, but someone told me not to make a partition in Windows for the Ubuntu installation, so I removed that extra partition.  What I have exactly is a Seagate 2 TB internal drive which is partitoned like this and are both NTFS: (C) Windows, which only has my Windows OS and Programs, (D) Data - has all of my docs, pics, vids, etc.  (C) has 292 GB total and (D) has 1.53 TB.  I just want to dual boot Ubuntu and Windows 7 and if Ubuntu isn't for me, I would like to be able to remove it without messing up my Windows 7 install.  Thanks for your help.

---

### Post by Quarkrad on 2015-08-19
I will defer to Bucky Ball as he has more experience than me but I have your setup.  In your scenario I created a new partition (made it ntfs - easy option) whilst in win7 splitting up your D drive - it is showing to be 1570GB so you have enough space.    So ....  you land up with three partitions on drive 1, C, D, and the new partition you create - let's call it E; give E a label name like ubuntu.  You don't have to do it this way but this is the method I have done a number of times.  You will get advice on the specifics of the Ubuntu install but when you get to the point where you install Ubuntu on drive 1 you already have a partition to use (it is E called Ubuntu).  You will reformat this partition to Ext4 and install Ubuntu on it including an extra partion called swap.  This is all easy stuff and you will be hand held through it - it is very easy. However, Bucky Ball may advise on a different method

---

### Post by Quarkrad on 2015-08-19
Secure boot is a win8 feature so that explains why you only have Quick Boot.   Have read of this **[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)** and come back if it is confusing/OK - it seems your pc is booting in EFI mode but it would be good to confirm.  When you come to install Ubuntu you will use the Something Else option not the Alongside Windows but that detail will come later.  If you boot into your bios you should be able to tell whether your machine is booting in uefi mode.

---

### Post by Bucky Ball on 2015-08-19
Don't make a partition for Ubuntu in Windows, no. It is pointless. Ubuntu can't be installed on any partition Windows can create (normally). Just leave unallocated (free) space. Rule of thumb? Manipulate Windows partitions with Windows, Linux ones with Linux. 

Yep, switch off secure boot. It equates to hibernate and if it is on you will basically have a locked drive/partition. You may need to do that by booting into Windows and switching it off. If it is in BIOS, switch it off there also.

@Quarkad: Yes, EFI. See previous page of posts. :)

---

### Post by Quarkrad on 2015-08-19
Have a look at this video  - **[https://www.youtube.com/watch?v=46FtBpv6Bjk](https://www.youtube.com/watch?v=46FtBpv6Bjk)**  To me the audio is a bit annoying but it covers the basics including some important things you need.  Although Linux Mint is being installed much of the graphics is the same as a Ubuntu install.  Have a look and let us know if you are comforable.

---

### Post by scottinpa40 on 2015-08-20
Thanks for all the help that you have given me.  I actually am now dual booting Ubuntu & Windows 7 now, but I had a problem.  I put the Ubuntu install on my (D) Data partition and it erased my data, which luckily I have a backup of.  What I wanted to do was have Ubuntu on a separate partition but it didn't work.  I didn't think it would erase it but I learned a lesson!

---

### Post by Quarkrad on 2015-08-20
For future reference - the first step should have been, whilst in win7, to shrink D to say, half it's size (or what ever size you want) to create an area of unallocated space (let's say this unallocated space is 60GB).  Then you insert the ubuntu CD or usb stick, reboot and install ubuntu.  During the install process you choose **Something Else** and install Ubuntu into the 60GB unallocated space (at the same time formatting it to ext4).  At this point you need to shrink (what was D) and create another partition (probably formatting to ntfs so win7 can see it) and put back what was on D back onto your HD.

---

### Post by scottinpa40 on 2015-08-20
OK, I understand now, thanks!

---

### Post by kurt18947 on 2015-08-20
I'm not at all familiar with secure boot, efi and such so no comment there. If you just want to 'play around' a bit with various distros, have you just tried running the live CD/USB without trying to install? Live USBs are much faster in live mode than CDs/DVDs.  It'll be somewhat slower and not fully functional but you can get a basic feel for how it works without touching your hard drive at all. I've also installed to a larger (16 GB+ at least) flash drive. If it installs and boots, you have a fully functional though slower[SUP]*[/SUP] install that can be updated, have printers installed etc. If you really want to be safe you could unplug/remove your hard drive so you don't install to it and overwrite what's there now. Disabling the existing hard drive in BIOS setup might work as well, I've never tried that.

If you had a 'conventional' BIOS setup I'd recommend a boot-repair disk or flash drive. I don't know if boot-repair works with UEFI/GPT systems. Boot repair did work on a system with a hybrid BIOS that already had Windows 7 installed as a 'conventional' BIOS.

[SUP]*[/SUP] Sorry if you already know this - flash drive writes are quite a bit slower than flash drive reads and USB2 flash drives are slower than USB3. I've never tried a 'real' install on a USB3 flash drive plugged into a machine with a USB3 port.

---

### Post by yancek on 2015-08-20
>   I put the Ubuntu install on my (D) Data partition and it erased my data

Expected behavior as I pointed out in my previous post when you mentioned installing Ubuntu on your "C" partition.  Good you had the backup.  Also, Linux won't run on a windows filesystem nor will windows run on a Linux filesystem.

From your post, this apparently was accidental as you didn't know which partition was which so you probably need to familiarize yourself with Linux naming conventions for drives/partitions.  You won't see "C" or "D" drive in Linux.  Also in Linux drive commonly refers to the physical hard drive rather than a partition while the terms are used interchangeably by windows users.

---

### Post by scottinpa40 on 2015-08-20
OK thanks for the info.  The Ubuntu install seemed to be working fine until I put a few pictures into the Pictures folder - now when I click to view the pictures in the folder, it won't allow me to view them.  It just goes back to the desktop.  The strange thing is that I'm able to open and view videos and documents.  The system then froze up completely not long after that and none of the keyboard or mouse wouldn't work, I had to do a forced shutdown.  Any ideas as to what could be happening?

---

