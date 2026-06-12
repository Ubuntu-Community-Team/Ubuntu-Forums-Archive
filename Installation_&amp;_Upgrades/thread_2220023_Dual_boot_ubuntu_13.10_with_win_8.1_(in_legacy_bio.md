---
title: "Dual boot ubuntu 13.10 with win 8.1 (in legacy bios mode)"
date: 2014-04-26
forum: Installation &amp; Upgrades
---

### Post by thedon710 on 2014-04-26
Hi, 
I'm running win 8.1 pro on Acer Aspire V3-772G. The BIOS mode is Legacy. I tried booting into Ubuntu 13.10 64bit with a USB and also, DVD. The booting media is detected in my BIOS, but after the screen with two icons at the bottom (one resembles a virtual keyboard and another, a man - guess these represent accessibility settings) the screen goes black. My laptop gets stuck after that and I need to restart it using the power button. Kindly help.

Thanks in advance!

---

### Post by oldfred on 2014-04-26
You may do better with 14.04 as many updates for new hardware have been included. Especially Haswell or 4th Gen Intel chips.

Did you reinstall Windows in BIOS/Legacy mode? 

Often the black screen is a video issue. What video card/chip do you have?
If dual video that is a separate issue.

With nVidia you need nomodeset. At accessibility icons, keyboard & person press any key then f6 & choose nomodeset. But if Intel other options are usually required.

       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
        [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
    
I think these were all UEFI installs:
 How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)
Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Added new msata drive post #3
[http://ubuntuforums.org/showthread.php?t=2174844](http://ubuntuforums.org/showthread.php?t=2174844)
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)
Acer UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64 June 2012
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)

---

### Post by thedon710 on 2014-04-27
Thanks!

I'll try with 13.10 initially. 

I had Windows 8 preinstalled when I bought the laptop and I installed Windows 8.1 Pro separately, which I guess is in Legacy bios mode (knowing by msinfo32).
 I have an Nvidia Geforce GTX760M along with Intel HD Graphics. And I'm not using dual video.  
Any tips regarding these?

And yeah. let me try the solutions that you have linked me to.

---

### Post by thedon710 on 2014-04-27
update: live booted from dvd,chose nomodeset, and booted to ubuntu with a few doubtful screens. Have posted the screenshots in sequence.
[ATTACH=CONFIG]252563[/ATTACH][ATTACH=CONFIG]252560[/ATTACH][ATTACH=CONFIG]252559[/ATTACH][ATTACH=CONFIG]252558[/ATTACH][ATTACH=CONFIG]252562[/ATTACH]

Though the boot was successful, the third and fifth screens puzzle me! What is the problem?

---

### Post by thedon710 on 2014-04-27
[ATTACH=CONFIG]252565[/ATTACH]

I tried installing Ubuntu for a dual boot setup, on an SSD partitioned as shown in the picture (created the 10GB partition-New Volume for Ubuntu). I live booted from an USB and started the process. 
At the step where we need to mention the drive for installation, the Windows partition wasn't detected. The whole SSD was shown to be free, without any partition table.
Help me out!

---

### Post by Luke M on 2014-04-27
Since you reinstalled Windows, you may have both MBR and GPT (from the previous installation) partition tables, confusing the ubuntu installer.

---

### Post by thedon710 on 2014-04-27
> **Luke M said:**
> Since you reinstalled Windows, you may have both MBR and GPT (from the previous installation) partition tables, confusing the ubuntu installer.Oh! Then how do I solve the issue?update: I verified using Disk Management. Disk0 (SSD that I want to install Ubuntu on) is MBR and Disk1(my hard disk - 1TB) is GPT. Hence that shouldn't mess up with Ubuntu installation because my SSD is MBR right?

---

### Post by Luke M on 2014-04-27
> **thedon710 said:**
> Oh! Then how do I solve the issue?update: I verified using Disk Management. Disk0 (SSD that I want to install Ubuntu on) is MBR and Disk1(my hard disk - 1TB) is GPT. Hence that shouldn't mess up with Ubuntu installation because my SSD is MBR right?

I don't know. Which disk had the preinstalled Windows? Run gparted or gdisk in ubuntu and see if they tell you that you have MBR and GPT on the same disk.

---

### Post by thedon710 on 2014-04-27
> **Luke M said:**
> I don't know. Which disk had the preinstalled Windows? Run gparted or gdisk in ubuntu and see if they tell you that you have MBR and GPT on the same disk.

Guess the SSD had the Windows 8 installation. Opened Gparted in live boot and it came up with an error message that said - gpt tables are found on dev/sda... no fake msdos something... I'm guessing this would be the solution:
[http://askubuntu.com/questions/388315/cant-format-or-delete-partitions-in-pendirve-cause-of-gpt-table-error](http://askubuntu.com/questions/388315/cant-format-or-delete-partitions-in-pendirve-cause-of-gpt-table-error)

I deleted the GPT leftovers using fixparts. Yep! Could see the partitions of the SSD in Gparted now, that I had made in Windows. Will try installation now!

---

### Post by oldfred on 2014-04-27
If hard drive is gpt and you want to install on it. It needs an efi partition for UEFI boot or a bios_grub partion for BIOS boot. I often suggest when setting up a new hard drive to include both so later you can change boot mode, if hardware is UEFI capable or drive may get moved to a newer system. UEFI suggest efi partition should be first on drive, although Windows makes it second or third, but still near beginning of drive.

I do not yet have UEFI system, but partition all drives with gpt as I will not have Windows. If you want Windows in BIOS mode then that drive and only that drive has to be MBR. Windows only boots from gpt partitioned drives with UEFI. 
Ubuntu will boot from gpt partitioned drives with UEFI or BIOS if correct supporting partitions are on drive.

---

### Post by thedon710 on 2014-04-27
Well I don't seem to have anything related to UEFI. :D From what I have read and tried since these issues came up, guess Win8 was installed first on GPT with UEFI. After that Win8.1 was installed on MBR, with Legacy BIOS. So now all I had to do was clean up the GPT leftovers with fixparts, and go on with the installation. Am I getting it right?

> **thedon710 said:**
> update: live booted from dvd,chose nomodeset, and booted to ubuntu with a few doubtful screens. Have posted the screenshots in sequence.
[ATTACH=CONFIG]252563[/ATTACH][ATTACH=CONFIG]252560[/ATTACH][ATTACH=CONFIG]252559[/ATTACH][ATTACH=CONFIG]252558[/ATTACH][ATTACH=CONFIG]252562[/ATTACH]

Though the boot was successful, the third and fifth screens puzzle me! What is the problem?

Can you clarify about the error and pixelated screens?

---

### Post by oldfred on 2014-04-27
Many of the video issues with Intel were fixed in 14.04. With nVidia you still need nomodeset.
Which video chip is system booting with? 
With Intel and 13.10 you probably need some of the boot options suggested above in link to ubfan1 in post #2.
If nVidia the nomodeset should work to at least get you into a low resolution screen so you can instal nVidia drivers.

---

### Post by thedon710 on 2014-04-28
Finished installing and everything's works fine. But I had these issues during LIVE BOOT.

Using nomodeset, I successfully live booted to Ubuntu. But during the booting process, I got the error screen and then the pixelated screen(both appeared for a second or so, and then Ubuntu came up and everything was fine). And, the green pattern on the pixelated screen is my logo (ACER) :P 
Why do they occur and how do I solve them?

Also,
How do i detect which video chip is used for booting?
ubfan1's post concerns UEFI systems right?
How can I install nVidia drivers in my case?

---

### Post by oldfred on 2014-04-28
Is this a dual video system?
ubfan1's suggestions apply for both BIOS & UEFI. Although even the same system may not need same settings if booted in different mode. 

I think the newest nVidia driver in 14.04 does not need bumblebee.
But to install nvidia go to system settings, software and drivers tab.

May not be most current info:
 Updates to nVidia Prime with 14.04 (only)
[http://www.phoronix.com/scan.php?page=news_item&px=MTU0MDI](http://www.phoronix.com/scan.php?page=news_item&px=MTU0MDI)
Newest nVidia Prime with 13.10 testing may run hot, but option to bumblebee
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)

---

### Post by thedon710 on 2014-04-29
> **oldfred said:**
> Is this a dual video system?
ubfan1's suggestions apply for both BIOS & UEFI. Although even the same system may not need same settings if booted in different mode. 

I think the newest nVidia driver in 14.04 does not need bumblebee.
But to install nvidia go to system settings, software and drivers tab.

May not be most current info:
 Updates to nVidia Prime with 14.04 (only)
[http://www.phoronix.com/scan.php?page=news_item&px=MTU0MDI](http://www.phoronix.com/scan.php?page=news_item&px=MTU0MDI)
Newest nVidia Prime with 13.10 testing may run hot, but option to bumblebee
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)


No mine's not a dual video setup. Just my laptop. 
Will read through ubfan1's post and  give updates if anything turns out good!
And I would just go in for 14.04 directly for the nVidia prime stuff. Seems more worthy than bumblebee :P

Can you explain about the 'X' window,x.org server,etc? Have no idea whether they are related or entirely different. I happened to come across them and got confused. 
P.S. 1. Don't know whether I'm getting those terms right. 2. Explanation in noob terms would be great :P 
Thanks a lot for your patience! :)

---

### Post by oldfred on 2014-04-29
I swear they said several years ago they were doing away with xorg settings. But they still are around.
[http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)

When my system was new back in 2006/2007 I had to manually go into the xorg file and change from nv to nvidia to change drivers. There also are/were settings to get video to match monitor. But that is now all automatic with most systems. Some with mulitple monitors may still have to change settings manually.

Even my 2006 system auto configures xorg file or other files. Nvidia drive knows my monitor is an old HP1903 and what settings are correct for that.

---

### Post by thedon710 on 2014-04-29
So the X system is something like a template for various applications' GUI? And x.org is just a file that stores the display configuration and such stuff?

---

### Post by oldfred on 2014-04-29
Not really related to GUI, but to hardware configuration for display.

GUI is the software and would use the display settings.

---

### Post by thedon710 on 2014-04-30
> **oldfred said:**
> Not really related to GUI, but to hardware configuration for display.

GUI is the software and would use the display settings.

Understood! :)

---

