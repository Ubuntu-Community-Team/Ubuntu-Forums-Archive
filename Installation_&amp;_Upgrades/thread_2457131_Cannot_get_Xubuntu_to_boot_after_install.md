---
title: "Cannot get Xubuntu to boot after install"
date: 2021-01-26
forum: Installation &amp; Upgrades
---

### Post by josh-q on 2021-01-26
I have a small mini PC with an eMMC drive. The Bios supports legacy and EFI booting. Downloaded current 64 bit Xubuntu 20.10. Using Rufus to make my boot USB sticks

When I use Rufus to make an MBR USB stick, I set the BIOS boot option to "Legacy",  the stick will boot, it will install, and when I reboot, the computer see's no drive and just goes to BIOS screen
When I use Rufus to make a GPT/UEFI USB stick, I set the BIOS boot option to "UEFI", the stick will boot, it will install, and when I reboot it just flashes some text over and over and never actually boots

If I go to the "Custom" setup in the installer, I delete every partition there, go to make anew partition, and every time I try to pick next the installer complains about something. 

I just want Xubuntu to install and boot. I don't care about BIOS vs UEFI and this partition or that partition. How do I do this to keep it simple?

---

### Post by grahammechanical on 2021-01-26
Is this intended to be a dual boot on this mini PC? Dual booting with Windows requires that Xubuntu/Ubuntu be installed in the same mode as Windows was installed. Both installations must be either UEFI or Legacy/CSM.

Here are the Ubuntu instructions for making an Installation USB memory stick using Rufus.

[https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview)

Notice section 4 where it says:

> The default selections for Partition scheme (*MBR*) and Target system (*BIOS (or UEFI-CSM)*) are appropriate (and are the only options available).

According to the pictured dialog box the Target System is set at Bios (or UEFI-CSM). And that is said to be appropriate. You seem to be selecting one or the other. I see no mention in these instructions to do that.

These are the selections for creating the bootable USB installation medium. Different choices will be made for installing on the eMMC drive.

[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

Regards

---

### Post by josh-q on 2021-01-26
> **grahammechanical said:**
> Is this intended to be a dual boot on this mini PC?
No, just Xubuntu


> **grahammechanical said:**
> Here are the Ubuntu instructions for making an Installation USB memory stick using Rufus. [https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview) 
The instructions are not correct. I am using Rufus 3.13. When I choose the Xubuntu ISO, it puts that ISO filename in the in the "Boot Selection" drop down. If I chage it tp "FreeDOS" it just makes a bootable USB disk with FreeDOS and no Xbunutu. You cannot choose FreeDOS and select the Xubuntu ISO

> **grahammechanical said:**
> According to the pictured dialog box the Target System is set at Bios (or UEFI-CSM). And that is said to be appropriate. You seem to be selecting one or the other. I see no mention in these instructions to do that.
If I leave "Partition Scheme" set to MBR and "Target System" to BIOS or UEFI (which is the defaults) Xubunutu will install off the USB but upon reboot the install drive will not be seen and I just get to the BIOS screen. If I change "Partition Scheme" to GPT, and "Target System" to UEFI (no CSM) which is the default, Xubunutu will install but will not boot, it just flashes a line on the screen over and over


Any idea how to make this work?

---

### Post by T6&amp;sfpER35% on 2021-01-26
> [COLOR=#000000]I just want Xubuntu to install and boot. I don't care about BIOS vs UEFI and this partition or that partition. How do I do this to keep it simple?[/COLOR]
just download the ISO [here]("https://torrent.ubuntu.com/xubuntu/releases/focal/release/desktop/xubuntu-20.04.1-desktop-amd64.iso.torrent") , burn it to a disk with Xfburn and boot the disk.
i could never get a bootable USB stick to work , maybe i'm just to dumb.
disks never failed me

---

### Post by josh-q on 2021-01-26
So I started over again. I used Rufus to make a fresh USB stick. Patition Scheme was set to MBR. Target System was set to BIOS or UEFI. I created the stick. 
In the computers BIOS I set the Boot Mode to Legacy

I am now at the screen I need to pick where to install Xubuntu. I selected "Something Else". I am then looking at a screen showing the partitions. I deleted all of them so I just have one chunk of free space. I selected the free space and clicked the + button. It gives a default size for the partition. It says "Type for the new partition" and has "Primary" or "Logical". I am leaving it on Primary. It then says "Location for new partition" and it lists "beginning of this space" and "End of this space". I leave it on "Beginning of this space. 

Next there is a drop down that says "Use as" with a bunch of options that I have no idea what any of them mean. Then below that it says "Mount point" and again I have no idea what goes there. 

What do I put on this screen so this just works like a normal computer?

---

### Post by T6&amp;sfpER35% on 2021-01-26
you should select clean install or something like that , not something else.
then it'll automatically delete windows and install xubuntu . dont choose to resize partitions or anything leave everything at default

ps. should backup anything you want from windows to external source

---

### Post by josh-q on 2021-01-26
> **3nd said:**
> you should select clean install or something like that , not something else.

When I do that, Xubuntu installs, and then does not boot.

---

### Post by josh-q on 2021-01-26
I tried following the directions on [https://www.avoiderrors.com/complete-guide-install-xubuntu-linuxos/](https://www.avoiderrors.com/complete-guide-install-xubuntu-linuxos/)

When I click Install it yells at me there is no EFI boot partition set up, even though this is not an EFI USB stick and there is no EFI setting in the BIOS, but OK?

This should not be this hard. Why in the world is any operating system in 2021 using partitions? They are a legacy concept from the 1960's when the location of your data on a hard drive matter because it was a spinning platter. We all have SSD's now. Drop the whole concept of partitions. And while on the topic of insanely outdated technology concepts, no one Dual Boots anymore. It's an outdated concept. There are a plethora of free virtualization solutions out there for every platform. It's 2021. If you need another system you virtualize it. Drop all this garbage about dual booting and boot managers and all this stuff that is currently keeping me from actually using the OS

Why does it feel like I am stepping back in time 50 years every time I try to get Linux to work?

---

### Post by T6&amp;sfpER35% on 2021-01-26
if you boot from disk it'll be a "live" session. look at desktop there should be a install icon. click it xubuntu will install.
at some point it'll tell you to remove removable media (the disk) before it boots

---

### Post by ajgreeny on 2021-01-26
The default "clean install" that you are talking about is, I assume, the option to "Use the whole disk" and allow the installer to create the partitions that are necessary?
Can you confirm this please.

I know nothing about Rufus nor how it deals with UEFI vs BIOS, so perhaps someone else who does know can help here as it may be that the partition table on the eMMC is not correct for using an eMMC drive with UEFI which is what you should be using.

Can you also tell us if you have **msdos** or **gpt** partitioning on the eMMC, as I think you will need gpt for such a new disk. If you're not sure boot to the live Xubuntu system from the USB and then use command ```
sudo fdisk -l
``` in terminal and show us what output you get.

---

### Post by T6&amp;sfpER35% on 2021-01-26
> [COLOR=#000000]The default "clean install" that you are talking about is, I assume, the option to "Use the whole disk" and allow the installer to create the partitions that are necessary?[/COLOR] if asked at me , yes that's what i mean

---

### Post by josh-q on 2021-01-26
> **3nd said:**
> if you boot from disk it'll be a "live" session. look at desktop there should be a install icon. click it xubuntu will install.
at some point it'll tell you to remove removable media (the disk) before it boots


I boot from the USB stick, and I have an option, "Try Xubuntu" or "Install Xubuntu". I click Install Xubuntu

---

### Post by josh-q on 2021-01-26
> **ajgreeny said:**
> 
I know nothing about Rufus nor how it deals with UEFI vs BIOS, so perhaps someone else who does know can help here as it may be that the partition table on the eMMC is not correct for using an eMMC drive with UEFI which is what you should be using.

Rufus lets you pick either. Neither of them actually work

---

### Post by T6&amp;sfpER35% on 2021-01-26
try my disk method , with the link provided.
i installed it like that and nowhere did it ask about UEFI or BIOS and what not

---

### Post by CelticWarrior on 2021-01-26
With Rufus select the options for UEFI/GPT.

In the firmware (UEFI) settings select UEFI only.

Boot a live session, open Gparted, select the eMMC drive then at the Device menu > Create new partition table... Select "GPT".

Proceed to install and preferably select the option "erase and install"/"use the whole disk (you got the idea)... Otherwise, if manually partitioning make sure to create an ESP (EFI System Partition), FAT32 formatted and with size ~100MB (make it larger if you want but not necessary for a single OS), then the / root partition and this is ALL you need.

Yes, this is the exact opposite of everything you've been doing. It's because forcing Legacy/CSM mode in 2021 is ridiculous and has exactly ZERO advantages.

---

### Post by josh-q on 2021-01-26
> **CelticWarrior said:**
> With Rufus select the options for UEFI/GPT. In the firmware (UEFI) settings select UEFI only.
Proceed to install and preferably select the option "erase and install"/"use the whole disk (you got the idea)... Otherwise, if manually partitioning make sure to create an ESP (EFI System Partition), FAT32 formatted and with size ~100MB (make it larger if you want but not necessary for a single OS), then the / root partition and this is ALL you need.

I did that. When the system was done installing it rebooted and all it showed was a black screen with some line of text on it (something like /dev/blkpmmc1lp/ something something) that would just flash over and over. I will try the Live CD "Gparted" whatever step and if that doesn't work I'm just done with Linux for another couple of years and hope someone learns how to make this usable without a degree in 1960's computer science. 

> It's because forcing Legacy/CSM mode in 2021 is ridiculous and has exactly ZERO advantages.

I'm not forcing anything. I tried Legacy/CSM mode, it didn't work. I tried GPT/UEFI mode, IT DIDN'T WORK.

---

### Post by josh-q on 2021-01-26
> **3nd said:**
> try my disk method , with the link provided.
i installed it like that and nowhere did it ask about UEFI or BIOS and what not

The device does not have a CD drive. It's 2021. No one uses CD's anymore.

---

### Post by tea for one on 2021-01-26
> **josh-q said:**
> I boot from the USB stick, and I have an option, "Try Xubuntu" or "Install Xubuntu". I click Install Xubuntu

Why not click "Try Xubuntu" and test all your hardware?

If it functions to your satisfaction, then try and install Xubuntu.

---

### Post by T6&amp;sfpER35% on 2021-01-26
> [COLOR=#000000] It's 2021. No one uses CD's anymore[/COLOR]
 i do  
oh and another thing that'll blow your mind  ,millions of people has installed various linux distros with no effort.
so yeah , carry on bashing linux cause **you're** unable to install it

---

### Post by CelticWarrior on 2021-01-26
> **josh-q said:**
> I did that. When the system was done installing it rebooted and all it showed was a black screen with some line of text on it (something like /dev/blkpmmc1lp/ something something) that would just flash over and over. I will try the Live CD "Gparted" whatever step and if that doesn't work I'm just done with Linux for another couple of years and hope someone learns how to make this usable without a degree in 1960's computer science. 


No, you didn't. You haven't had the time to try it so, please, if you want help the bare minimum required is honesty about your efforts regarding our suggestions here. Whining and posting ridiculous statements and veiled threats will lead you nowhere. Millions of people around the world of all ages and wlks of life have installed and are using Ubuntu or other Linux distros and the vast majority of them in UEFI mode, the standard at least since 2012 (much older actually, it started in Apple's hardware). 

And it's not a "live CD"... I explicitly mentioned a live session in the sequence of the instructions to make an installation USB. Gparted is included in said live session, no need for additional media

> I'm not forcing anything. I tried Legacy/CSM mode, it didn't work. I tried GPT/UEFI mode, IT DIDN'T WORK.
If you explicitly select Legacy only in UEFI settings you've changed the default, therefore forcing a Legacy installation. And you also made an USB that only boots in Legacy mode. Howe is this NOT forcing?
UEFI mode is the defaults and recommended mode for all UEFI based hardware such as yours. Legacy mode is still there - not for long though - to enable support for (very old) OSes that don't understand UEFI (Windows Vista or older, for example). 

So, when you say you "GPT/UEFI mode" and "it didn't work", what happened exactly? Which of the steps in the previous instructions you weren't able to perform? Please explain in detail and respecting everyone else here trying to help you. That means no shouting, insulting, etc.

---

### Post by josh-q on 2021-01-26
> **CelticWarrior said:**
> If you explicitly select Legacy only in UEFI settings you've changed the default, therefore forcing a Legacy installation. And you also made an USB that only boots in Legacy mode. Howe is this NOT forcing?

The first thing I did was explicitly set the Boot Mode to UEFI in the BIOS and made a GPT/UEFI USB stick to boot from. When it didn't work I tried the Legacy way. The computer supports both. I don't care which way I use, as long as it works. 

> 
So, when you say you "GPT/UEFI mode" and "it didn't work", what happened exactly? Which of the steps in the previous instructions you weren't able to perform? Please explain in detail and respecting everyone else here trying to help you. That means no shouting, insulting, etc.


[LIST]
[*]I booted into my BIOS and set the Boot mode to UEFI on the computer
[*]I launched Rufus and selected "GPT" under "Partition Scheme" and UEFI under "Target System"
[*]I selected the ISO and made a bootable USB stick
[*]I booted off the USB stick, when it got to the part about where to install, I picked the "Delete everything and Install Xubuntu" option I think it was the third one down
[*]Xubuntu installed
[*]At the end of the install it said "remove the installation media and press enter". I did that. The computer rebooted.
[*]When it booted up, I got a black screen with a line of text that said something like "/dev/blkplmmclp1/something something something" and had some numbers and I think the words "blocks" there. It just kept flashing that and doing nothing.
[/LIST]

After that failed to work, THAT is when I tried the MBR/Legacy route. I wasn't trying to force any particular path. I just want it to boot up and it is astonishing that it is this hard to make that happen.

---

### Post by yancek on 2021-01-26
>  This should not be this hard. Why in the world is any operating system in 2021 using partitions?

I  think you have a lot of reading to do to understand these concepts.  If  you've been a windows user previously, it's understandable as windows  hides this information from users.  A default install of windows 7, 8  and 10 uses multiple partitions for different purposes.  Virtual  software is useful but slower than actual hardware.

In one of your posts you indicate that you do not know what to do during the install when it asks:  Use as, that woulds be the filesystem type which all operating systems use and the default for Ubuntu is ext4 which will be one of the options in the drop down menu.  The Mount point option is required and the only one you need to select from the drop down menu is the symbol:  /  which is for the root of the filesystem.

I'm not sure if you understand that this forum consists of a group of volunteers who spend their free time trying to help other people.  There are tens of millions of people around the world from 12-80 who have successfully installed Ubuntu and its derivatives so it's not the operating system, it's the user that is the problem.  Your negative attitude and complaining are not going to get you much help.

---

### Post by CelticWarrior on 2021-01-26
> 
[LIST]
[*]When it booted up, I got a black screen with a line of text that said something like "/dev/blkplmmclp1/something something something" and had some numbers and I think the words "blocks" there. It just kept flashing that and doing nothing.
[/LIST]


After a correct installation in UEFI mode and by correct I mean no error reported in the end, check UEFI settings again. In the Boot menu there are two settings that must be correctly selected - they usually are after the installation but not always -, one is the drives order, the other is OS selection. Both can have other names, of course, so consult you user's manual or online documentation to be sure. At the drives order the one where the ESP resides should be the first. Then, at the OS selection, it should say explicitly "Ubuntu". 

The above should be the correct and necessary settings. Other than those we also recommend disabling Secure Boot and Fast Boot (again, any firmware is unique and names vary). If still not working please post the error message in its entirety, not the "something something", because that "something" is likely crucial to understand the root cause.

---

### Post by QIII on 2021-01-26
josh-q:  Please cool your jets, tone down the tenor of your posts and harken to the tuition provided here.

Take a deep breath.

I wonder why you would be using 70 year old technology like SSDs.  Non-volatile solid state data storage existed in the '50s and it took us to the moon in the 60s.  But the devices were not really well suited to what we could call a "hard drive interface".  That, I know from my own experience, existed at least by 1978.  Back then it was bulky and expensive, so you may not have encountered it.  But it was there then.  Like you said, it's 2021.

Partitions?  You may only recently have become familiar with them if you have been a Windows user.  But Windows uses partitions, too.  In the world of Windows, they go by the misnomer "x:\ drive" on a single device.  So Windows users -- other than many good admins -- are often unfamiliar with the term "partition".  Is Windows still in the dark ages, I wonder.  Windows still even has a "partition manager". Linux just uses the appropriate terms:  "device" and "partition".  So do Unix and BSDs.

It may come as a shock to you that things like mechanical drives, CDs, DVDs and, dear me, *floppy and diskette drives*, still exist.  But they do.  And they are still used.

I am going to point out again something that was said above:  YOU are clearly having issues.  We aren't saying otherwise.  But you have made the hasty generalization (dabbling in some ***argumentum ad populum*** along the way) and leapt to the conclusion that the experiences of all users are reflected in your own.  That is a common logical fallacy for humans, but it is not the case.

Please dispense with the histrionics.  That will go a long way towards getting better help and it will also guard against what might become for you the uncomfortable attention of the forums Staff.

---

### Post by josh-q on 2021-01-27
> **CelticWarrior said:**
> With Rufus select the options for UEFI/GPT.

Done

> In the firmware (UEFI) settings select UEFI only.

Done

> Boot a live session, open Gparted, select the eMMC drive

I did that, and a bunch of partitions were there. So I deleted them all, then I hit the green checkmark to Apply the changes, and it deleted everything. 

> then at the Device menu > Create new partition table... Select "GPT".

Done

> Proceed to install and preferably select the option "erase and install"/"use the whole disk (you got the idea)... 

The only two options were "Erase disk and install Xubuntu" and "Something Else". I picked "Erase Disk and install Xubuntu". It installs, I get to the screen where it says "Please remove your installation media and press "Enter", I do so

The computer reboots, I see the Xubuntu logo and the little spinning circle, and then the screen goes blank and it's flashing the following line over and over again:

[B]/dev/mmcblk1p2: clean, 213093/3784704 files, 2388749/15136256 blocks
[/B]

And it just sits there blinking that over and over again. This is exactly what it did last time I tried to do the UEFI boot and install method

---

### Post by CelticWarrior on 2021-01-27
The good news is there's no problem with the installation.
```
[B]/dev/mmcblk1p2: clean, 213093/3784704 files, 2388749/15136256 blocks
[/B]
```
is NOT an error, it's a normal system boot process message.

The bad news is what should happen right after that - loading the Desktop Environment - isn't happening. But this has nothing to do with the installation itself.
Please post the hardware specification as detailed and accurate as you can so we can take a look, namely the graphics. Needless to say keep the installation as is for the moment. The troubleshooting can and should be done from there.

---

### Post by josh-q on 2021-01-27
> **CelticWarrior said:**
> The good news is there's no problem with the installation.
```
[B]/dev/mmcblk1p2: clean, 213093/3784704 files, 2388749/15136256 blocks
[/B]
```
is NOT an error, it's a normal system boot process message.

The bad news is what should happen right after that - loading the Desktop Environment - isn't happening. But this has nothing to do with the installation itself.
Please post the hardware specification as detailed and accurate as you can so we can take a look, namely the graphics. Needless to say keep the installation as is for the moment. The troubleshooting can and should be done from there.


I just checked back and now it's just a black screen and not even showing that message

It's a Minisforum N36. [https://www.gearbest.com/mini-pc/pp_009980509379.html](https://www.gearbest.com/mini-pc/pp_009980509379.html) seems to have a good layout of the specs. The graphics are Intel HD Graphics 400.

[TABLE="width: 1000"]
[TR]
[TH="align: center"][FONT=OpenSans]General[/FONT]
[/TH]
[TD]Brand: MINISFORUM
Model: N36
Type: Mini PC
System: Windows 10
CPU: Intel Celeron N3060
Core: Dual Core
GPU: Intel HD Graphics 400
RAM: 4G RAM
RAM Type: LPDDR3
ROM: 64G ROM
Maximum External Hard Drives Capacity: 2TB
Color: Black[/TD]
[/TR]
[TR]
[TH="align: center"][FONT=OpenSans]Media Supported[/FONT]
[/TH]
[TD]Decoder Format: H.263,H.264,H.265,HD MPEG4
Video format: 4K,ASF,AVI,DAT,FLV,ISO,M2TS,M4V,MKV,MOV,MP4,MPEG,MPG,RM,RMVB,TP,TS,VOB,WMV
Audio format: AAC,ALAV,APE,DTS,FLAC,MP2,MP3,OGA,OGG,TrueHD,WAV,WMA
Photo Format: BMP,GIF,JPEG,JPG,PNG,TIFF
Support 5.1 Surround Sound Output: Yes[/TD]
[/TR]
[TR]
[TH="align: center"][FONT=OpenSans]Product Details[/FONT]
[/TH]
[TD]5G WiFi: Yes
WIFI: 802.11 a/b/g/n/ac, Dual-band WiFi 2.4GHz/5GHz , Dual wireless antenna
Bluetooth: Bluetooth 4.2
Power Supply: Charge Adapter
Interface: 3.5mm Audio,DC 12V,RJ45,TF card,USB2.0,USB3.0,VGA
Antenna: Yes
Language: English,French,Germany,Italian,Japanese,Simplified Chinese,Spanish
DVD Support: Yes
HDMI Version: 1.4
Other Functions: 3D Games,3D Video,DLNA,ISO Files,Miracast,NTSC,Others,PAL
External Subtitle Supported: Yes
HDMI Function: CEC,HDCP,HEC
Power Consumption.: 36W
RJ45 Port Speed: 1000Mbps[/TD]
[/TR]
[TR]
[TH="align: center"][FONT=OpenSans]Firmware Information[/FONT]
[/TH]
[TD]System Bit: 64Bit
WiFi Chip: AC3165
System Activation: Yes[/TD]
[/TR]
[TR]
[TH="align: center"][FONT=OpenSans]Power Requirement[/FONT]
[/TH]
[TD]Power Type: External Power Adapter Mode
Power Input Vol: 12V
Suggest Input: 12V 3A
Power Adapter Input: 100-240V / 50-60Hz[/TD]
[/TR]
[/TABLE]

---

### Post by CelticWarrior on 2021-01-27
> **josh-q said:**
> I just checked back and now it's just a black screen and not even showing that message

It's a Minisforum N36. [https://www.gearbest.com/mini-pc/pp_009980509379.html](https://www.gearbest.com/mini-pc/pp_009980509379.html) seems to have a good layout of the specs. The graphics are Intel HD Graphics 400.
Indeed. Those should just work. I've installed dozens of Intel based miniPCs, mostly Celerons like yours, and never had an issue whatsoever.
Are you using HDMI or the old VGA?
Although it shouldn't matter for Intel Graphics but just in case disable Secure Boot and Fast Boot, if applicable.
Does yours have some weird options for video output like Legacy/UEFI (unrelated with the boot process settings, this are video output specific settings that can be mixed and matched)? You may need to test options there. Also do you see any settings for virtual screens/desktops? Some firmwares have them and those are a pain to deal with. Typical of some early Celeron Jxxxx series, this is the only exception where the recommended settings are "UEFI+CSM" (boot priority to UEFI, of course) but video output as "Legacy", othewise you may end up with a virtual/phantom second screen or some other weird behavior.

---

### Post by josh-q on 2021-01-27
> **CelticWarrior said:**
> Indeed. Those should just work. I've installed dozens of Intel based miniPCs, mostly Celerons like yours, and never had an issue whatsoever.
Are you using HDMI or the old VGA?

HDMI. 

> Although it shouldn't matter for Intel Graphics but just in case disable Secure Boot and Fast Boot, if applicable.

Neither option exists in my BIOS

> Does yours have some weird options for video output like Legacy/UEFI (unrelated with the boot process settings, this are video output specific settings that can be mixed and matched)? 

There are 3 settings, one for Storage, One for Video, and one for Other PCI devices. All were set to Legacy. I switched them to UEFI, and the same thing happened except now there is a line saying **/dev/mmcblk1p2:recovering journal **above the other line


> You may need to test options there. Also do you see any settings for virtual screens/desktops? Some firmwares have them and those are a pain to deal with. Typical of some early Celeron Jxxxx series, this is the only exception where the recommended settings are "UEFI+CSM" (boot priority to UEFI, of course) but video output as "Legacy", othewise you may end up with a virtual/phantom second screen or some other weird behavior.

No settings for virtual screens or desktops in the BIOS

---

### Post by CelticWarrior on 2021-01-27
> **/dev/mmcblk1p2:recovering journal**
isn't a problem either. It likely happened due to an abrupt shutdown. Please keep in mind that even without a GUI the OS *is* working. If you do CTRL+ALT+F1 (maybe others like F2, etc.) you'll likely see a login prompt. The quoted message is unrelated with the UEFI settings and unfortunately those solved nothing. I'm still baffled.

Regarding the other options, Fast Boot isn't mandatory in the UEFI standards so you're probably right. OTOH, Secure Boot is mandatory. Not always explicitly mentioned by name though. Try to find some "OS type" setting as this is another way many vendors implemented the Secure Boot option. In it you may find references to "Windows 8/10", "Windows 7" (rarely others like XP/Vista but it can happen), "Linux", "Android"... That being the case always select "Linux" or "Android".

If the above settings don't help getting into a working desktop, then please CTRL+ALT+F1 and login (first type your username - enter - then your password - enter -) and run 'startx'. Please report back the error message.

---

### Post by josh-q on 2021-01-27
> **CelticWarrior said:**
> isn't a problem either. It likely happened due to an abrupt shutdown. Please keep in mind that even without a GUI the OS *is* working. If you do CTRL+ALT+F1 (maybe others like F2, etc.) you'll likely see a login prompt. The quoted message is unrelated with the UEFI settings and unfortunately those solved nothing. I'm still baffled.

Yeah in order to reboot I have to pull the power plug out of the device, so it is sbruptly hsutting down

When I reboot, it starts flashing those messages, if I press  CTRL+ALT+F1 I do see a login prompt for a fraction of a second, then the screen goes blank and it shows the **/dev/mmcblk1p2:recovering journal + ****/dev/mmcblk1p2: clean, 213093/3784704 files, 2388749/15136256 blocks **message

I cannot find anything in the BIOS related to operating systems or anything referencing Windows or Linux

---

### Post by CelticWarrior on 2021-01-27
It seems there are lots of problems running Linux in that device: [https://bbs.minisforum.com/threads/cannot-boot-linux.1249/](https://bbs.minisforum.com/threads/cannot-boot-linux.1249/)
But even there some users reported success. Now, those with problems reported a different situation than yours. Yours feel more like a problem with the graphical subsystem. I have no further suggestions other than update the firmware (UEFI) but, as usual with this "alternative" brands it appears there's no update released yet and probably never will be. Funny thing, all the ones that I've installed before including the one I'm using to type this, never needed any update, all with firmware versions spanning from 2014 to 2019, all working absolutely fine, all unbranded silver/grey/black little boxes imported from Aliexpress, all cheaper than yours.

Try asking for help in their forums - you can and probably should reference the link above and explain the problem isn't the same, describe it as you just did in the previous post - to see what they say about it.

---

### Post by josh-q on 2021-01-27
I went back into my Bios, and saw under my Boot options it had "Ubuntu" listed as the first AND second boot options. So I disable the second boo option so there was only one Ubuntu listed, and the system booted to a desktop. 

Once booted I got an error message "System software problem detected, would you like to Report?" I reported. I then ran all the accumulated updates, rebooted, and got the same error message, but after clicking Report it goes away and it seems to be working now.

---

### Post by CelticWarrior on 2021-01-27
:guitar:

---

### Post by josh-q on 2021-01-27
[COLOR=#000000]I get an error message "System software problem detected, would you like to Report?" on every boot. Should this be a concern? Where can I look for what the error is?
[/COLOR]

---

### Post by CelticWarrior on 2021-01-27
Not really. Errors happen and tend to be corrected with updates.
There are logs you can check but that dialog also should have some dropdown menu that when expanded should at least inform which package has generated the error.

---

### Post by T6&amp;sfpER35% on 2021-01-27
> [COLOR=#000000]"System software problem detected, would you like to Report?"[/COLOR]

[https://itsfoss.com/how-to-fix-system-program-problem-detected-ubuntu/](https://itsfoss.com/how-to-fix-system-program-problem-detected-ubuntu/)

in terminal ,run
```
sudo rm /var/crash/*
```


glad you got it booting ok now , that error thing is minors
:)

---

### Post by josh-q on 2021-01-27
> **3nd said:**
> 
in terminal ,run
```
sudo rm /var/crash/*
```


glad you got it booting ok now , that error thing is minors
:)


That seems to have stopped the message from displaying again.

---

