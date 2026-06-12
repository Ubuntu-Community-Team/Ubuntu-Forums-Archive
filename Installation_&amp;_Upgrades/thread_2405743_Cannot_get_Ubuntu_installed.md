---
title: "Cannot get Ubuntu installed"
date: 2018-11-10
forum: Installation &amp; Upgrades
---

### Post by courth03 on 2018-11-10
Hi everyone. I am fairly new to Ubuntu, but I have used it in the past and have it on a separate desktop that does nothing but run a folding program. I am having a heck of a time trying to get Ubuntu installed on my main desktop. I want to install it alongside my existing Windows 10 installation, however I am having a very hard time doing so. I have even tried installing it on a separate hard drive altogether, but can't make any headway.

I created the bootable USB media within my existing Ubuntu installation on this laptop I am typing on and my installation will get to the part where I select the prompts, but there lies the problem. When I get to this point my keyboard and mouse will not work at all. I don't even see a mouse cursor on the screen and hitting tab on the keyboard does nothing. I have tried multiple different keyboards and every USB port on my desktop even going as far as installing a separate USB 2.0 card in the desktop and still see the same thing. Specs are as follows.

CPU: Ryzen 7 2700X
Motherboard: Asus X470-Pro
RAM: 16GB DDR4 G.Skill TridentZ
Main SSD: Western Digital M.2 500GB
Secondary SSD: Western Digital M.2 1TB

Anyone have any ideas? I have gone through my BIOS and made sure Legacy USB is enabled in hopes maybe it's a USB 3.0 thing on the motherboard ports, but that doesn't seem to make a difference either. I do have PS/2 ports on my motherboard, but I don't have access to any of those mice or keyboards with that connector type unfortunately. Is there maybe a setting in BIOS that I need to enable that I am just missing? Any help would be greatly appreciated as I would love to use Ubuntu full time and leave Windows only for games.

---

### Post by dinkidonk on 2018-11-10
On your mother board there is a USB2 header, usually used with a connector to/on the enclosure - have you tried those with USB2 legacy support enabled? What do you mean by "where I select the prompts"? If you have keyboard available in the list where you select "Start Ubuntu" (and others), then a long shot could be to highlight the "Start Ubuntu" item, hit "e" on the keyboard and in the first line/command change "quiet splash" to "nomodeset quiet splash" and hit CTRL+X to boot with that.

---

### Post by oldfred on 2018-11-10
If Windows is UEFI, you really want Ubuntu booting in UEFI boot mode.
And how you boot install media is then how it installs. So you need to boot install media in UEFI boot mode.
Only a few systems seem to let you boot in UEFI mode with Legacy enabled. Most then only boot in Legacy/CSM/BIOS boot mode.

What version of Ubuntu, you may need the very newest and even then perhaps a newer kernel & drivers as you have very new hardware.

       Ubuntu 18.04 with updates from ppas
Ryzen 7 2700 / Ryzen 7 2700X / Core i7 8700K Linux Gaming Performance With RX Vega 64, GTX 1080 Ti
[https://www.phoronix.com/scan.php?page=article&item=ryzen-2700-gaming&num=1](https://www.phoronix.com/scan.php?page=article&item=ryzen-2700-gaming&num=1) 
            Asus B350M-A needs newer kernel that 18.04 default
[https://ubuntuforums.org/showthread.php?t=2391892](https://ubuntuforums.org/showthread.php?t=2391892)
[https://ubuntuforums.org/showthread.php?t=2390660&p=13799816#post13799816](https://ubuntuforums.org/showthread.php?t=2390660&p=13799816#post13799816)

Only if willing to experiment, you can try the new Disco Dingo. Just installed a couple of hours ago after they fixed an issue with installer & it looks like it has 4.18 kernel. But my system is now a couple of years old which is the sweet spot for Linux as just about every little issue has been fixed.

---

### Post by courth03 on 2018-11-10
> **dinkidonk said:**
> On your mother board there is a USB2 header, usually used with a connector to/on the enclosure - have you tried those with USB2 legacy support enabled? What do you mean by "where I select the prompts"? If you have keyboard available in the list where you select "Start Ubuntu" (and others), then a long shot could be to highlight the "Start Ubuntu" item, hit "e" on the keyboard and in the first line/command change "quiet splash" to "nomodeset quiet splash" and hit CTRL+X to boot with that.

Yep I have a USB 2.0 expansion slot connected to that USB header on the motherboard and have tried the keyboard and mouse attached to those and still they do not appear during setup. What I mean by "where I select the prompts" is when the setup process starts and you go through the prompts I can't use the mouse or keyboard.

> **oldfred said:**
> If Windows is UEFI, you really want Ubuntu booting in UEFI boot mode.
And how you boot install media is then how it installs. So you need to boot install media in UEFI boot mode.
Only a few systems seem to let you boot in UEFI mode with Legacy enabled. Most then only boot in Legacy/CSM/BIOS boot mode.

What version of Ubuntu, you may need the very newest and even then perhaps a newer kernel & drivers as you have very new hardware.

       Ubuntu 18.04 with updates from ppas
Ryzen 7 2700 / Ryzen 7 2700X / Core i7 8700K Linux Gaming Performance With RX Vega 64, GTX 1080 Ti
[https://www.phoronix.com/scan.php?page=article&item=ryzen-2700-gaming&num=1](https://www.phoronix.com/scan.php?page=article&item=ryzen-2700-gaming&num=1) 
            Asus B350M-A needs newer kernel that 18.04 default
[https://ubuntuforums.org/showthread.php?t=2391892](https://ubuntuforums.org/showthread.php?t=2391892)
[https://ubuntuforums.org/showthread.php?t=2390660&p=13799816#post13799816](https://ubuntuforums.org/showthread.php?t=2390660&p=13799816#post13799816)

Only if willing to experiment, you can try the new Disco Dingo. Just installed a couple of hours ago after they fixed an issue with installer & it looks like it has 4.18 kernel. But my system is now a couple of years old which is the sweet spot for Linux as just about every little issue has been fixed.

I checked how Windows is booting and it is booting in Legacy mode which is how I am trying to boot the Ubuntu install media. This is with Ubuntu 18.10, the newest version.

---

### Post by oldfred on 2018-11-11
Little strange that you have a very new system and using the now 35 year old BIOS/MBR configuration.
But that is your choice, if it works. Do not know AMD well, but I think all the other installs were UEFI.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  
Microsoft originally did not want any drivers written for older systems, so users had to use newer Windows in UEFI mode. But many large users had Windows 7 and wanted the capability to upgrade hardware, at least in short run. Do drivers are usually available.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) 
            UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by courth03 on 2018-11-11
Thank you for the links, I will check them out and Thank you for continuing to try to help me. I do really appreciate it. I may go ahead and try reinstalling Windows in UEFI mode and then try Ubuntu in the same mode. Not a huge deal to reinstall Windows as I don't have much on the OS anyways. I'll give that a whirl first and then let you know.

---

### Post by oldfred on 2018-11-11
Both Windows & Ubuntu installers should have two boot modes in UEFI boot menu.
And how you boot install media UEFI or BIOS is then how it installs.

Be sure to have good backups as conversion to gpt will in effect erase drive.

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

### Post by courth03 on 2018-11-12
Here's an update.

I formatted a USB drive with Windows 10 on it in UEFI mode and installed Windows 10 on my 500gb M.2 drive using UEFI mode. Everything went smoothly and I was back running Windows in no time. I also formatted a separate USB drive with Ubuntu 18.10 on it in UEFI mode. I booted to that USB drive and chose "test Ubuntu without installing". I was able to get loaded into the live environment and my keyboard worked, but I had no mouse cursor. The weird thing is my mouse was working because when I'd move it all the way to the side of the screen I'd be able to see the icons on the dock light up, but there wasn't a cursor being rendered. I did choose the option to install Ubuntu, but going through the prompts I wasn't able to complete it because when I go to the part where you can size the partitions I had no way to move the slider only using a keyboard since I couldn't tell where my cursor was since it didn't render. Any ideas why that may be happening? Do you think my system and parts could be a bit too new at the moment and I'll just have to wait a bit?

---

### Post by oldfred on 2018-11-12
If mouse is actually working (you see icons light up) then the mouse pointer may be same color as background or something similar. I have not adjusted mouse settings for ages, but know there are some settings.

You should use Windows to shrink the NTFS partition & reboot immediately so it can run chkdsk.
You can use gparted to create new partition(s) and just use keyboard to enter sizes.

---

