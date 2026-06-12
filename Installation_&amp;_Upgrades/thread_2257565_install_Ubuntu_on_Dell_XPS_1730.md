---
title: "install Ubuntu on Dell XPS 1730"
date: 2014-12-20
forum: Installation &amp; Upgrades
---

### Post by John_Combe on 2014-12-20
I brought an old XPS 1730 and tried using Ubuntu 14 and 13 on it with a live usb drive with persistence created via Universal USB installer, but I could not get it to work. It booted from the usb but afterwards with 14.04 the screen flashed though white, orange, green, etc colors for several minutes. With 13.04 it booted as well from usb but only a blank screen (no image at all).
I looked on the board and it seems that Dell computers seem to require some more work to run due to closed drivers required for some hardware. How do I get Ubuntu to run on a Dell XPS 1730?

---

### Post by oldfred on 2014-12-20
Dell is actually very good. For some of the newer systems, the released the sputnik updates for 12.04. And all those updates then were in later releases of Ubuntu.

You have to dual video issue.
In BIOS can you choose which video you boot with Intel or nVidia?
You may need nomodeset if booting with nVidia chip.

With my system, I needed nomodeset for live installer and added to grub for first boot or until I installed the nVidia proprietary drivers from the Ubuntu repository.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.

How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Do not use obsolete versions of Ubuntu like 13.04.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by John_Combe on 2014-12-20
It is a NVIDIA GeForce 8700M GT video card from the specifications. I only brought the laptop because the seller actually kept all the discs and documentation, a very important thing if I wanted to use Windows XP on it. Not a lot of people seem to think keeping the original packaging, discs, and documentation is important, so finding someone selling a laptop and keeping everything that came with it was a surprise.

---

### Post by John_Combe on 2014-12-21
Okay I looked at those pages and I do not know how to use the information. After getting the Linux menu up (try, install, advanced options, help, etc) what do I do? I went into the help menu but while reading the list and seeing what was available the screen blinked two or three times then went into going though the color spectrum again. I need to be told what to do so I can do it fast in order to prevent the color spectrum thing again. It is a Dell XPS 1730 laptop with a NVIDIA GeForce 8700M GT video card so I need step by step instructions, as I can not do it by myself even with resources pointed out by oldfred. I used a Ubuntu 14.04.1 desktop iso that was put on a usb drive with a persistence file of 4 Gb so I could make changes that stick, though I do know major changes like updating some components can not be done or the live usb would be rendered useless.

---

### Post by oldfred on 2014-12-21
So the live installer started to work with the nomodeset setting and then went crazy?
Was this what you did?
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I have used nomodeset and with that setting never had issues. But my system was a totally different model nVidia card. 
There may be settings in BIOS?

Once you get live installer working and you have have it working reasonably well or you may not be able to install and make similar fixes to install.

How large is hard drive? How are you planning on splitting drive between Windows & Ubuntu.
Generally with Vista and later better to use Windows to shrink the Windows partition and reboot immediately to allow Windows to update itself to its new size and run chkdsk.

Are you familiar with partitions? Not Windows "drives".  Or do you just want the default install of / (root) and swap with whatever sizes the installer selects. 
If you want more than default then you have to use Something Else and set sizes of partitions, mount like / or /home and format like ext4.
       [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Older 12.04 but install process is same.
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 

If you also reinstall, you must use Something Else to use existing / (root) partition. 

 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

---

### Post by John_Combe on 2014-12-21
I want to try Ubuntu 14 without installing it. The issue is what command string to use to test it out without installing it when the computer in question is using a NVIDIA graphic card. I have looked at those pages and can not figure out what command to use to activate NOMODESET. I have not used linux before so what command to use to activate NOMODESET is, all I have gotten to is pressing F1 then pressing F2 and upwards and not seeing this NOMODESET that is mentioned by you and those pages you gave links to. All I know is that a command string is supposed to be entered after "boot:" is at the bottom of the screen after pressing F6 or F7, but I can not figure out what the command is as those pages confused me. All I want to do is test Ubuntu 14 out on the XPS 1730, without installing it so I can see if I like it, but I apparently need a special command string because of the NVIDIA graphic card.  
What I need is the command string to type after getting to the "boot:" prompt that activates testing without installing Ubuntu and activates NOMODESET, something I have looked at those pages for and could not find. It may be obvious to a Linux user and installer what to do but I have only used Windows XP/7/8 before so I have no clue what to type.
I know you are trying to help but I have never used Linux before, only Windows.

---

### Post by oldfred on 2014-12-21
First are you starting in UEFI boot mode or BIOS boot mode.
       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If purple screen press the infamous 'any' key while the tiny icons are are shown, then press f6. arrow down to nomodeset.
IF grub menu (UEFI or first boot after install) you have to manually add it.


 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by John_Combe on 2014-12-21
I had to press TAB not E to bring up a long string of code where I pressed the spacebar then typed nomodeset. Now it worked (GUI) appeared, but now I am curious if I can update or change the display drivers/app to have the display go higher than 1024X768. I am comfortable with 1440X900 resolution, but given that it is a LiveUSB with persistence (4GB) I am not sure if trying to update the display drivers or whatever is used in ubuntu would render the LiveUSB useless.

---

### Post by oldfred on 2014-12-21
Not sure if you can update video on live installer or not. 

Anything your download is reinstalled on every boot and you cannot update any program that is built into the installer as it always installs the standard configuration and after install then you can update.

---

### Post by Doug S on 2014-12-22
I have a Dell XPS 1730. While it doesn't normally run Ubuntu, I have test run Ubuntu on it before. I downloaded Desktop 14.04.1. made a ISO DVD, and it seems to run fine with no display issues.

---

### Post by John_Combe on 2014-12-23
Ok this can be closed as in my case after downloading NVIDIA drivers I was able to get the highest resolution possible, and I got it to work after some research on other forums.

---

