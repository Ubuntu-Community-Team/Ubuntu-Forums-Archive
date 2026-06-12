---
title: "Only able to boot into bios after efi install of Ubuntu 14.10 on new hd"
date: 2014-12-28
forum: Installation &amp; Upgrades
---

### Post by julia4 on 2014-12-28
Hello, I've previously installed Ubuntu successfully on a much older computer in legacy bios mode, but I finally upgraded and built a new pc over the holidays which has an asus z97-a motherboard with uefi bios with secureboot enabled. I wanted to try to take advantage of the uefi and secureboot if I could after successfully testing my hardware on a Ubuntu live usb uefi flash drive. (I'm only installing Ubuntu 14.10 on a new sata hd, not Windows or any other OS.) 

So after much researching, I used gparted in live mode to create a new gpt partition on a blank sata hd and an efi boot partition (with efi boot flag enabled). Then used the Ubuntu installer "something else" setting to create the rest of my partitions. In all, an efi boot partition, swap and root (ext.4) (primary, no logical partitions) on sda drive, just Ubuntu 14.10 with very simple partitioning (and secureboot enabled in bios)....After installing, I shut down the computer, removed the usb flash drive and started up the computer. After showing the normal Asus startup message on how to access the bios, it went to a blank, black screen, then a blinking cursor for a few seconds, and finally automatically switched to the bios. It never showed any sign of grub or Ubuntu when booting up. I did see Ubuntu listed in the boot list in the bios, so I know it installed.

I wondered if I pointed the installer to the wrong place for grub (the main sda partition, instead of sda1 where the efi boot partition was-- I couldn't decide earlier which partition to point the installer for the bootloader and left sda as default location.) So, I rebooted back into the live usb and in gparted deleted all the partitions and started over. Redid the partitions the same way, except this time I pointed the installer to the sda1 efi boot partition....When I tried restarting the computer, once again grub never appeared to load, and I was automatically switched to the bios settings. 

After searching for a solution, my questions: 
1. From live usb, I looked into etc/fstab and it looks like Ubuntu installed properly unless I'm mistaken?  Should I try to run boot-repair? I don't want to make anything worse.

Or...

2. Does this sound like secureboot is preventing grub and Ubuntu from booting? If so, should I delete the partitions again and try another fresh install with secureboot disabled?  If yes, would it be better to try an efi install with the gpt partition or go back to using legacy mode? 

Any help/advice would be greatly appreciated!

---

### Post by grahammechanical on 2014-12-28
I would say that if secure boot was the problem then the Ubuntu live session would not be allowed to load. That is what secure boot is for. To prevent unauthorised executable files for running. It is your choice whether you install Ubuntu in EFI mode or Legacy mode. It does not matter if Ubuntu is the only OS.

> 
[LIST]
[*=left][FONT=inherit][Create a LiveDVD or LiveUSB]("https://help.ubuntu.com/community/LiveCD#How-To_LiveCD_Ubuntu") of Ubuntu (>=12.04.2) **64bit**.[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]In your BIOS, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows8, also [disable FastStartup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html").[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]Boot your PC using the LiveDVD or LiveUSB and choose "Try Ubuntu". If you get a **Secure boot** or **signature** error, you may wish to disable [SecureBoot]("https://help.ubuntu.com/community/UEFI#SecureBoot") as described [here]("https://help.ubuntu.com/community/UEFI#SecureBoot"), then retry to boot the disk. [FONT=inherit][/FONT][/FONT]

[*=left]Install Ubuntu from the Live CD/DVD or Live USB in the usual manner, then reboot the PC.
[/LIST]


> [COLOR=#333333][FONT=Ubuntu]Having a PC with EFI firmware does not mean that you need to install Ubuntu in EFI mode. What is important is below: [FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.[FONT=inherit][/FONT]
[*=left][FONT=inherit]if the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too. Eg if your computer is old (<2010), is 32bits, or was sold with a pre-installed Windows XP.[FONT=inherit][/FONT][/FONT]

[*=left]if Ubuntu is the only operating system on your computer, then it does not matter whether you install Ubuntu in EFI mode or not.[FONT=inherit][/FONT][FONT=inherit][/FONT]
[/LIST]
> [COLOR=#333333][FONT=Ubuntu]To install Ubuntu in EFI mode:[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left][FONT=inherit]Use a 64bit disk of Ubuntu. ([Ubuntu32bit cannot be easily installed in UEFI mode]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555"). This is a problem if 32-bit EFI is the only way your computer can boot, e.g. if you have a modern Intel Atom based laptop. In this case, you will need [a complicated work-around]("https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md").)[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]You might want to use an [EFI-only image]("https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_an_EFI-only_image") to avoid troubles with mistakenly booting the image and installing Ubuntu in BIOS mode. [FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]Use a supported version of Ubuntu. Support for UEFI appeared in 11.10, but has become more reliable in next versions. Support for UEFI[SecureBoot]("https://help.ubuntu.com/community/SecureBoot") appeared in 12.10 and 12.04.2.[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]Set up your firmware (BIOS) to boot the disk in UEFI mode (see the "[Identifying if the computer boots the HDD in EFI mode]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode")" paragraph below)[FONT=inherit][/FONT][/FONT]

[*=left]Then:[FONT=inherit][/FONT][FONT=inherit][/FONT]
[LIST]
[*=left]nothing special is required if you use the automatic installer of Ubuntu ("Install Ubuntu alongside others" or "Erase the disk and install Ubuntu"). Important: if you have a pre-installed Windows and you want to keep it, do not choose "Erase the disk and install Ubuntu".[FONT=inherit][/FONT][FONT=inherit][/FONT]
[*=left][FONT=inherit]if you use the manual partitioning ("Something else"), the difference is that you will have to set the /boot/efi mount point to the EFI partition. And if there was not any EFI partition on your HDD, you first will have to create it (see the "[Creating an EFI partition]("https://help.ubuntu.com/community/UEFI#Creating_an_EFI_partition")" paragraph below).[/FONT]
[/LIST]
[/LIST]


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

That wiki is as far as my experience with UEFI goes.

Regards.

---

### Post by julia4 on 2014-12-28
Thank you very much, [COLOR=#000000]grahammechanical[/COLOR], for your help. Unfortunately, I think I pretty much did all that already. I have a sinking feeling this may be some setting in the bios itself that may need changing. I'll keep researching. If anyone else has any more ideas, they will certainly be welcome.

---

### Post by Dennis N on 2014-12-28
I built a system with Asus H97M-Plus motherboard. Almost the same chipset as you have, except H97 does not overclock. M means it is a micro-ATX board. There is no Windows installed, only Linux.  Installation was done in UEFI mode. I left the secure boot enabled. Secure boot would not prevent grub from booting when you have the signed kernel (which you automatically get when you install with secure boot enabled).

As to the place to install grub, it doesn't matter if you put sda or sda1. Both result in grub installed to the EFI system partition on sda. I know because I have installed 4 OS on my machine so far, and tested both sda and sda1 as choices. 

As to UEFI-bios settings, in the Boot Section, Fast Boot is disabled, "Launch CSM" is enabled, Boot device Control = "UEFI and Legacy OPROM". Boot from Network Devices = "Ignore" (this one I changed from the default); Boot from Storage Devices = "Legacy OPROM first"; Boot from PCI-E/PCI.. = "Legacy OPROM first."  Secure Boot is "Windows UEFI mode". Most of these were the defaults.

Hope this answers a couple of your questions.

---

### Post by julia4 on 2014-12-28
Thank you so much, Dennis for the info and ideas from your own experiences! I still can't boot into Ubuntu normally, but I was able to match my settings to yours, which helped me rule that out. One less possibility on the list. After racking my brain, the only other thing I can think of, is maybe my hard drive isn't UEFI compatible, as I think I've heard some hardware still may not be. I think I'll try a legacy mode install tomorrow to see if that helps instead. Thank you again!

---

### Post by oldfred on 2014-12-28
I just built a system with the Asus-ar which is the same as yours and in fact the UEFI/BIOS is the same.

I had a lot of settings to change to get it to boot flash drive in UEFI mode. And you have to boot flash drive in UEFI mode to install in UEFI mode. I do partition in advance and created both the efi partition and bios_grub partition so I could change if need be.
The first settings was "Windows" and "Other OS" which I think is really the secure boot setting. I found all the other UEFI settings under the CSM sub menu.
I try UEFI & CSM with UEFI first to boot flash drive and it still booted in BIOS mode. Only when I set to UEFI only did I get flash drive to boot in UEFI mode.
I had to turn on boot from storage devices and full UEFI boot first.

I updated UEFI to then current 1304, have not checked since.

I also changed to next boot after AC failure or cold boot to be normal not fast boot. I was afraid if fast boot is always on, I might not be able to get back into system. I later changed fast boot to 3 sec so I can always get into it and changed grub to 3 sec. System with SSD now boots faster than UEFI and grub.

I can go back and take screen shots of settings if you need them. I was thinking of doing some of that just for my own info.

---

### Post by Dennis N on 2014-12-29
> I just built a system with the Asus-ar which is the same as yours and in fact the UEFI/BIOS is the same.
I'm curious what Asus motherboard model the "Asus-ar" is? You seemed to have to do a lot of adjustments to get it to work. Mine worked immediately with the defaults.

---

### Post by julia4 on 2014-12-29
@oldfred: Thank you for sharing your experience. I would very much appreciate your sharing the screenshots of your settings. I dug into the advanced bios settings, and I think I have them set correctly. I've experimented with different settings and always end up back in bios. Also, I manually booted UEFI flash drive listed in bios boot list on my 2nd install attempt to make sure it would install in efi mode. 

1. I found it odd that Ubuntu (installed, not Ubuntu on USB flash drive) was listed in the boot priority list in bios as a separate boot drive from my two new WD blue series 1TB hard drives (no SSD drive installed). Is that normal? (I've only formatted the 1st hd and installed Ubuntu on it. I was waiting until later to format the 2nd hd to use as an extra data backup drive. It's connected, but not formatted. Unless you think the system is balking at booting up if an unformatted extra drive is detected, which didn't seem likely to me?)

2. If I direct the system to list only uefi boot devices/drives, it only shows the Ubuntu listing in the boot priority list. The hard drives disappear from the list as if they are considered legacy devices. Thus my idea of maybe the hd isn't uefi compatible and needing to reinstall in legacy mode with a grub-bios partition. 

3. My bios is version 1205 which is one version behind 1304 if I remember correctly. I think a stability update was mentioned for 1304 on the Asus website and a performance update after 1304, but no major updates I remember? I was hoping to not have to update unless absolutely necessary as I hear it's a real pain, and I've never updated a bios before. As it's my 1st build, I'm nervous about making a mess of my bios and possibly having to restore it. 

4. I noticed the main secure boot setting to turn it on/off is grayed out. I read somewhere if I wanted to disable it, I would have to set a password to access the setting. I'm hoping it won't come to that. 

I will keep trying. Thank you everyone for the replies!  :)

@Dennis: If I remember correctly, I believe the Asus-ar was also a z97 series? At least, that was my impression when I was shopping for a motherboard.

---

### Post by oldfred on 2014-12-29
[http://www.asus.com/us/Motherboards/Z97AR/specifications/](http://www.asus.com/us/Motherboards/Z97AR/specifications/)

When I went out to update UEFI, the Asus seemed to show the same UEFI for the A model. The only difference as I understand is the video out ports and the salesman sold me the wrong one, or I did not notice details when I purchased it. My monitor is older, and only have DVI and VGA in. But the AR only has HDMI and Display port out. 

I did want to try the Intel video and eventually found a cable that converts from HDMI to DVI, but system is now against wall and difficult to change, so have not tried that yet. The reason I wanted to try Intel video is that my video cards are either my old 9600GT and a somewhat newer 620GT. And the reviews I read were that Intel, and both nVidia cards are about equal in performance. I do not game, so very high end performance is not a requirement.

In the next couple of hours I will reboot and see if I can get a good set of screen shots of configuration settings.

---

### Post by Dennis N on 2014-12-29
My bios says the version is 317 for the Asus H97, so maybe there is a difference there. Like I said, mine worked with the defaults on the initial startup. On mine, the drive entries in UEFI bios don't boot anything. I believe they are for Legacy installs that might be there. I have four OSes installed (Ubuntu flavors), but only one Ubuntu entry in the UEFI bios boot manager. The other three are accessible from grub menu only. This is because each new install overwrites the EFI system partition entry for the previous Ubuntu install and enters itself into the UEFI menu. I actually never need to use the UEFI bios boot manager to choose anything - its always a selection from grub.

@oldfred, 
Still curious on the model number of your ASUS board. Would like to check it out. If you are curious, my board is mentioned in my prev. post. From what I read, I believe H97 is the same as Z97 chipset, except no overclocking capability.

---

### Post by Dennis N on 2014-12-29
Is it this one?
[http://www.frys.com/product/8129255](http://www.frys.com/product/8129255)
Full size ATX!
I guess there is only one AR board. Only this one comes up in search, so you can disregard my asking for model. I found it. Sorry about that.

---

### Post by oldfred on 2014-12-29
It looks like when I added some screens to my favorites, they go moved from default location, so not sure now which menu they were under.

I have two more on USB ports, if they would help or let me know if you want something else.

It is nice that I can directly take screen shots in UEFI menu. It saves to flash in .bmp, so I converted with shotwell to png which also made them smaller so I could upload. Limit seems to be 5 files.

---

### Post by julia4 on 2014-12-29
Thank you, the screenshots definitely help. I recognize those settings. I think the only big difference I didn't try was the secure boot menu type as Other OS. I had that set to Windows UEFI. I was about to try a legacy install, but will give one more try with the EFI install and the setting of Other OS. Hopefully that will do the trick.

---

### Post by julia4 on 2014-12-29
Update: I finally got Ubuntu to boot successfully! :D  

For the record and any future readers: 
I tried two more installs: one with an EFI install and a second with legacy install on the gpt disc, the former with the EFI boot partition and the latter with only the Grub-bios partition instead. Neither worked. I gave up and went to my backup plan: using a live boot, I reformatted both drives to the classic ms-dos (MBR) format and used a dvd install of Ubuntu 14.10 in legacy mode. 

(Before I did the final legacy install, I made sure in the bios that the settings were for legacy hardware and "Other OS" instead of "UEFI Windows mode". I tried disabling secureboot manually, but it was grayed out, even after trying to set the bios admin and user passwords. So I left secureboot alone and didn't touch the secureboot keys.)  And in case it helps someone else, when installing Ubuntu 14.10, I used "Something Else" in partitioning and did a standard root, swap and home partitioning scheme with the default primary/logical partitions, using the whole drive. Then left the grub install to the default sda partition setting. That's it. 

Thank you again so much to those who replied! I have no idea why this worked, unless maybe my theory about my hard drive not being EFI compatible was correct? On the positive side, I'm no longer intimated by my system bios or creating partitions and learned a LOT. So, some good things came out of this experience. :)

---

### Post by Dennis N on 2014-12-29
Congratulations!

I see your UEFI install went out the window and you are back to old MS-DOS partitioning and standard MBR installation. I am a little surprised you could not install in Legacy mode to a GPT disk, however. I would have expected that to work. I used that method on another UEFI computer we have. And also since O.F. has his system working, that his settings did not work for you.

To make gpt work, it depends on bios, installer, and grub all supporting gpt. Since we have all three, its a mystery where the problem is. I don't believe gpt compatablilty is applicable to hard disks so that would not be the reason.

Good luck and enjoy your new computer!

---

### Post by julia4 on 2014-12-29
Thank you, Dennis! :)  Yes, I was surprised when the legacy install on a gpt disk didn't work either. If it wasn't the hard drive compatibility, then maybe a bios update would have fixed that (and it was my next plan if the MS-DOS legacy boot didn't work). I might try a bios update some day if I ever get my nerve up, but for now, I'm just elated something finally worked. 

The only other possibility that just occurred to me is maybe there was something wrong with the usb flash drive installer? After my old computer was taken apart, I borrowed a Windows computer to create the usb flash drive installation with the linux live usb creator using as source the Ubuntu 14.10 install dvd that was originally created in mint 17 xfce. Who knows?  Whenever I install ubuntu 15.04 in a few months, I'll try another UEFI/legacy install with a flash drive properly prepared in ubuntu to see what happens.

---

