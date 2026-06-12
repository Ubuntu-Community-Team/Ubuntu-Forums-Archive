---
title: "Install Ubuntu on new Machine, many failures"
date: 2018-07-25
forum: Installation &amp; Upgrades
---

### Post by seattlechris on 2018-07-25
I am attempting to install Ubuntu (18.04 LTS) on a new laptop I just purchased. At  the start it has no OS, but eventually I want to set it up as dual-boot  with windows. So far I've only attempted to install Ubuntu with  repeated errors. Boot-Repair utility did not fix things, but I have a  link to pastebin for the report generated, and I believe all the  critical specs on this new laptop listed below. 

What I have done:

After  many  attempts installing Ubuntu on this new machine (using a USB key) and  tracking down different possible errors Along the way many of the  shortcut keys or terminal commands have not worked as suggested in the  various threads that seemed to address the issues I was having. After  seeking other solutions, fixing some mistakes along the way, and  (hopefully) getting a better understanding on how things work, I believe  that most of my  previous problems had to do with the graphics card driver setup. Since I  had many dead-ends and questionable attempts at fixing it as I stumbled  along, I thought it was best to start (yet another) fresh install (wipe  the drive) and just do the steps that seemed correct. However this last  attempt leaves me with a black screen (after a brief dark purple  screen)  and no progress of loading, or at least seeing, anything. So  actually worse than how far I previously had gotten things. Attempting  to pull up the grub safe boot menu only brings me to a grub  terminal and I haven't been able to resolve things from there. I  attempted the Boot Repair, which did not resolve my issues. Looking over  the output of the Boot Repair report, I now wonder if there are left  over issues from my previous installs that I had believed would be  totally written over on later install attempts (I always selected to  wipe the whole drive on each install attempt). After many frustrations, I  am sad to say I'm at my wits end. 

Prior to my  efforts with this machine, my previous experience with installing Ubuntu is  when I managed to install a  dual-boot Ubuntu on my windows laptop that I had been using for the  past 8 years. In contrast, I didn't have much trouble with Ubuntu  install (after the long challenge of making enough room on the single  hard drive to be able to have both for dual-boot). Shocking to me, I  hardly ever had to boot up into windows  during the 6 weeks I was still using that laptop. I thought installing  on a new blank machine was going to  be easier, but that is not how it has turned out. 

## New Laptop ##

Make & Model: Clevo N870EK1 (also known as Sager NP6873)
Display (LCD): 17.3" 1920 x 1080 Full HD (16:9) Wide View Angle 72% NTSC IPS Matte Type Display
CPU: Intel Core i7-8750H Processor 2.2 Ghz (Max Turbo Frequency 4.1GHz), 9MB Smart Cache
GPU: NVIDIA® GeForce&#8482; GTX 1050 Ti w/4GB GDDR5
Memory: 16GB DDR4 2666MHz - 1 x 16GB
M.2 SSD Drive Slot 1: 500GB Samsung 970 EVO M.2 PCIe NVMe SSD
Hard Drive/SSD Slot 1: 500GB Samsung 860 EVO SSD
Keyboard:Full Color Programmable Backlit
OS: None


I  would like to install Ubuntu as the primary OS on the NVMe SSD (Samsung  970). I read somewhere that if I want to do dual-boot (with windows),  it might be good to put the other OS on a different hard drive (since I  have 2), but not dedicate all 500GB to the windows side of the system.  While the second hard drive has a slower connection, my experience with  Ubuntu so far says this probably won't matter and will still be faster  and better setup than my old dual-boot laptop that only had a  traditional hard drive. So far I haven't done anything for the windows  OS setup since I am waiting until I can get a less expensive copy from a  friend of a friend who works at MicroSoft. I mention this dual-boot  goal now in case it changes some choices I would make, and also I would  be happy to hear feedback if setting Windows on a partial portion of the  2nd drive is a good idea (which is much further in this process than I  have even had a hope to attempt yet). 

## Boot Repair Report ##

[URL="http://paste.ubuntu.com/p/j98t66XbkK/"]http://paste.ubuntu.com/p/j98t66XbkK/
[/URL]

Let  me know if other information would be helpful. I'm sad to say the  frustration with this install is fraying my brain and patience. I  appreciate what help I can get to setting up this new laptop with Ubuntu  and get back to enjoying it!

---

### Post by Topsiho on 2018-07-25
I don't think there should be any issue installing Ubuntu on a Clevo laptop, as many Clevo laptops are sold with Ubuntu as the OS.
So the source of the problem is somewhere else, and that is probably that the USB key is not good. You should have the **image** of the.iso file put onto it, not a copy of it. How you do that without Ubuntu or Windows I don't know, someone else might tell you this.
You want to dual boot together with Windows, Ubuntu as the primary OS. Great. But then you need to install Windows first! If you install Ubuntu first, and then Windows, you can not use Ubuntu, without hassle, as Windows overwrites grub, the program that lets you boot the computer in Ubuntu or in Windows.
So maybe you install Windows first, then create a USB-key for Ubuntu, using the .iso file of Ubuntu, and the disk creator in Windows (no idea what program that is), and then install Ubuntu. It is very unusual that installing Ubuntu goes haywire.

I have no experience with UEFI, someone else may tell you more about that. If you need this.

Topsiho

---

### Post by yancek on 2018-07-25
Did you mean to do an LVM install, do you know what LVM is/does?  If not, don't use it or do some research on how to install and use it.
Your sda drive (465GB) doesn't show any partitions and nothing appears to be installed, at least the common files and expected information from boot repair do not show.  Might be best to look at the official Uubntu documentation at the site below on dual booting with windows 10 and Ubuntu before you try again.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Some points to look for are whether you want to use GPT partitioning.  If you do, you need windows installed UEFI.  If you use the older Legacy/dos partitioning format, you can install windows after Ubuntu if you select the Custom installation option on windows but as pointed above, this will overwrite the MBR of Ubuntu Grub.  If you do an EFI install, that should not be a problem.  Best to read the doucmentation aboveas it has a lot more info.

---

### Post by oldfred on 2018-07-25
It looks like you have Ubuntu in UEFI mode on NVMe drive. Script does not fully parse NVMe drives.

Not sure if Windows gives option to install to separate drive. It may just overwrite Ubuntu.
If you have a way in UEFI to turn off the NVMe drive, then install Windows to HDD in UEFI mode. How you boot install media UEFI or BIOS is how it installs for both Windows & Ubuntu.

---

### Post by seattlechris on 2018-07-25
> **yancek said:**
> Did you mean to do an LVM install, do you know what LVM is/does? 
I did select this option. I admit it "sounds good" and did not do research on it. Kind of forgot I selected it. Does it seem likely to cause errors? 

> **yancek said:**
> 
Some points to look for are whether you want to use GPT partitioning.  If you do, you need windows installed UEFI.  


From what I have read, I will need to do windows installed in UEFI, therefore all other OS's on the machine should be in UEFI.

---

### Post by seattlechris on 2018-07-25
> **Topsiho said:**
>  I don't think there should be any issue installing Ubuntu on a Clevo laptop, as many Clevo laptops are sold with Ubuntu as the OS.
So the source of the problem is somewhere else, and that is probably that the USB key is not good. 

I remade a Ubuntu boot USBkey (using my old laptop running Ubuntu in dual-boot). I get the same roadblocks when attempting to install on the new machine. 

> **Topsiho said:**
> 
But then you need to install Windows first! If you install Ubuntu first, and then Windows, you can not use Ubuntu, without hassle, as Windows overwrites grub, the program that lets you boot the computer in Ubuntu or in Windows.
So maybe you install Windows first, ... 

I really don't want it to be true that I need to install windows first. I don't have access to a copy of windows OS for a bit longer. I have work I need to get done and things I need to setup on the Ubuntu OS on this new machine. Can I get confirmation from others that this will be a road block, because I was really counting on windows OS being installed later on.

---

### Post by seattlechris on 2018-07-25
> **oldfred said:**
> It looks like you have Ubuntu in UEFI mode on NVMe drive. Script does not fully parse NVMe drives.

Are you saying I can't have a boot drive on an NVMe drive? This does not seem right. At least for other OS's. 

I admit I am new to SSD drives in general and especially the NVMe drives, but a bit selling point is the quick boot up. Now I have a machine that has two SSD drives (with the NVMe drive as the boot drive). What do you mean "Script does not fully parse NVMe drives?"

---

### Post by seattlechris on 2018-07-25
I thought I would try the notes from the following section since I get the blank screen. 
Graphics Resolution - Upgrade/Blank Screen after reboot
[https://ubuntuforums.org/showthread.php?t=1743535](https://ubuntuforums.org/showthread.php?t=1743535)
The first step is to get into the Grub Menu. I've gone through all the options listed for how to do this, and each hits a roadblock as described below. 
-----------------------------------------
**[COLOR=#b22222]Option 1) [/COLOR]**Repeated shift keys (left or right) does not work
**[COLOR=#b22222]Option 2)[/COLOR]** Boot from LiveUSB: this line unclear, going to 2nd half of post #3 
  these are also steps required for next, and my notes of roadblock are below
**[COLOR=#b22222]Option 3) [/COLOR]**Forcing Grub to Show Menu, as posted here: 
[https://ubuntuforums.org/showthread.php?t=1743535&page=80&p=11469860#post11469860](https://ubuntuforums.org/showthread.php?t=1743535&page=80&p=11469860#post11469860)

It seems I can edit the etc/default/grub file, but I do get 2 warnings: 
    1) gedit WARNING: Set document metadata failed: Setting attribute metadata::gedit-spell-language not supported
    2) gedit WARNING: Set document metadata failed: Setting attribute metadata::gedit-encoding not supported

After that, sudo update-grub doesn't work, oh, I think we need to mount the system first

-- Mounting An Installed System From the LiveCD as instructed here: 
[URL="https://ubuntuforums.org/showthread.php?t=1743535&p=10740097#post10740097"]https://ubuntuforums.org/showthread.php?t=1743535&p=10740097#post10740097
[/URL]
  Uhh, I don't see that first screen when I boot, but 2nd is simliar (no funct keys)
  That said, I can set nomodeset (or acpi=off) with e = edit. 
When I navigate to the installed partition, there is no 'sdaX' (some letter for X) in dev directory
**[COLOR=#b22222]Option Final)[/COLOR]** reinstall Grub
Reinstalling Ubuntu brings me back to repeating all these problems. Should I try to format the hard drive and install Grub2 by itself?

---

### Post by oldfred on 2018-07-25
If you do not know LVM, I would start over. LVM is an advanced volume system, often used with servers. But it requires different tools for managing and is less well known. Those knowledgeable users do seem to like it as it does have some advantages.
       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM) 
    
If you have UEFI with gpt partitioning, then you can install Windows after Ubuntu. Even with BIOS you can install it after, but either requires you follow various procedures. 
Dual booting with Windows is usually not used with LVM.
Windows only boots from gpt partitioned drives with UEFI.
Windows only boots from MBR partitioned drives with BIOS.

How you boot install media, UEFI or BIOS is then how it installs for both Ubuntu & Windows. So if you want UEFI, always boot in UEFI mode. That may require selecting it for USB boot and making sure settings in UEFI are UEFI, not CSM/Legacy/BIOS or whatever your system calls it.

While a lot of info see link below in my signature for more info on UEFI. Particularly at end are terms & definitions or links to further definitions.

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

The Boot-Repair script just has not been updated to fully support showing all the details on NVMe drives. Systems work ok with NVMe drives. But many systems do require UEFI updates and some require SSD firmware updates.

There are some advantages of installing Ubuntu to one drive, and Windows to another. But not sure if that is possible. Some systems have UEFI settings to hide or turn off a drive which is what you would need to do to cleanly install Windows to a separate drive after Ubuntu on another drive.

---

### Post by seattlechris on 2018-07-31
Hey, I got it working! Thank you Topsiho, yancek, [COLOR=#000000]and especially Oldfred for your help! [/COLOR]Of all the branches of trying different settings, I thought I had already determined one to not work, but apparently, I skipped over something. Oldfred's last response made it easier to eliminate some "unkowns" I was considering as possible issues and got me back on track. Thank you!

---

### Post by seattlechris on 2018-07-31
On my first (few) attempts to install I had a problem of everything seeming fine for a few minutes, then mouse clicks and keyboard inputs would stop working. This was resolved by editing the command that calls up "Try Ubuntu Before You Install It" or "install" with the 'acpi=off' command (often 'nomodeset' is also suggested, but I didn't see this until later. I actually believe 'nomodeset' is probably the better option). 

After this was resolved, I would still have the OS freeze up whenever I did something to call up the "settings". This is where I spent a ton of time trying to fix things without realizing that I needed to fix the graphics card driver first. Also, by using 'acpi=off' instead of 'nomodeset', some other error checking methods may not have worked. 

Eventually, I got wise that the graphics card driver was an issue. Many of the routes suggested to fix this did not work. In one way or the other, the commands didn't work, or files were not where they were expected, or outcomes did not match what was reported. Apparently by this time I had tried so many different options, and read up on so many different levels of complexity, it all came to a mess and it was hard to think "what is the most basic straightforward setup" to get things working.

---

### Post by Topsiho on 2018-07-31
I am glad that you have solved this problem now. Congratulations.
One thing though. I suggested that you should install Windows first, and only after that you install Ubuntu. I am quite convinced this to be true, but things change in the run of time. Did you install Ubuntu first, and only after that install Windows? Without issue? No grub replaced by Windows?
Not that it worries me much as I never install Windows. My computers have never seen Windows. But I don't like to give false information :(
Topsiho

---

### Post by Topsiho on 2018-07-31
I have one computer that needed the option of "nomodeset". Didn't know why, but when I discovered this, booting from the LiveDVD was no problem. And after the installing of Ubuntu this option was added automatically. It had no videocard, the video part was done in the (AMD-)processor itself.
After I installed a dedicated videocard the nomodeset-option was not needed anymore. So probably, or possibly, the Clevo doesn't have a dedicated graphics card, and so needed the nomodeset-option?
Topsiho

---

