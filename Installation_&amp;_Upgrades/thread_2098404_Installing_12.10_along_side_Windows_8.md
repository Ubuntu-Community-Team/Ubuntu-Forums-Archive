---
title: "Installing 12.10 along side Windows 8"
date: 2012-12-26
forum: Installation &amp; Upgrades
---

### Post by colmeweb on 2012-12-26
So I have a new Toshiba Satellite C850D with windows 8 pre-installed, and I am trying to install 12.10 64 bit. Ubuntu's main site said that this version had a license in place to get through the secure boot but it still blocked me. I have turned off the secure boot feature, but I still can't load the live usb. When I select to boot from the usb there is a quick flash that I can't read and then a blank screen. The only way to get out of it is to hold down the power button till there is a hard shut down. I have seen some hints on how to do a wubi install, but I really don't want to do that. 

I have also seen some things that say I have to disable the fast/quick boot feature, but I couldn't find any of those features in my BIOS so I'm not sure how to do that.

---

### Post by colmeweb on 2012-12-26
So a quick update.

I changed the Boot Mode in my advanced Bios settings from UEFI to CSM and that allowed me to see the keyboard/vitruvian man screen, and I also hear the ubuntu drum sound, but the screen stays blank.

---

### Post by oldfred on 2012-12-26
If you have Windows pre-installed you have UEFI and Windows uses gpt partitioning. Wubi does not work with gpt partitioning, currently.

Be sure to shrink Windows using the Windows MMC, but do not create partitions with Windows. Use gparted or Ubuntu installer, or auto isntall into the unallocated space.

Back-up efi partition and your Windows.
       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Only now we can get to booting from flash drive. If you are getting drum sound it has booted but is having a driver issue, usually video driver.
What video card/chip do you have?

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

    How Boot-Repair works with UEFI systems - post 687 Dec 15, 2012
[http://ubuntuforums.org/showthread.php?t=1769482&page=69](http://ubuntuforums.org/showthread.php?t=1769482&page=69)

---

### Post by colmeweb on 2012-12-26
Thank you for the help. 12.10 is up and running but now there is an ongoing list to work through. 

First is the fact that my wireless is down it doesn't show up on the top panel or in the network settings. this is the output of lspci -nn

```
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 14h Processor Root Complex [1022:1510]
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Device [1002:9808]
00:01.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI Wrestler HDMI Audio [Radeon HD 6250/6310] [1002:1314]
00:10.0 USB controller [0c03]: Advanced Micro Devices [AMD] Hudson USB XHCI Controller [1022:7812] (rev 03)
00:11.0 SATA controller [0106]: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode] [1022:7801]
00:12.0 USB controller [0c03]: Advanced Micro Devices [AMD] Hudson USB OHCI Controller [1022:7807] (rev 11)
00:12.2 USB controller [0c03]: Advanced Micro Devices [AMD] Hudson USB EHCI Controller [1022:7808] (rev 11)
00:13.0 USB controller [0c03]: Advanced Micro Devices [AMD] Hudson USB OHCI Controller [1022:7807] (rev 11)
00:13.2 USB controller [0c03]: Advanced Micro Devices [AMD] Hudson USB EHCI Controller [1022:7808] (rev 11)
00:14.0 SMBus [0c05]: Advanced Micro Devices [AMD] Hudson SMBus Controller [1022:780b] (rev 14)
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] Hudson Azalia Controller [1022:780d] (rev 01)
00:14.3 ISA bridge [0601]: Advanced Micro Devices [AMD] Hudson LPC Bridge [1022:780e] (rev 11)
00:14.4 PCI bridge [0604]: Advanced Micro Devices [AMD] Hudson PCI Bridge [1022:780f] (rev 40)
00:14.7 SD Host controller [0805]: Advanced Micro Devices [AMD] Hudson SD Flash Controller [1022:7806]
00:15.0 PCI bridge [0604]: Advanced Micro Devices [AMD] Device [1022:43a0]
00:15.1 PCI bridge [0604]: Advanced Micro Devices [AMD] Device [1022:43a1]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 [1022:1700] (rev 43)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1 [1022:1701]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2 [1022:1702]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3 [1022:1703]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4 [1022:1704]
00:18.5 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6 [1022:1718]
00:18.6 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5 [1022:1716]
00:18.7 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7 [1022:1719]
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8723]
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)

```

And the output for iwconfig is
```

eth0      no wireless extensions.

lo        no wireless extensions.

```


The other issue is that when I boot my computer it goes straight to Ubuntu. No grub, no option for windows. I haven't looked into it yet because the wireless is more important, but if anybody knows a quick fix thats great too.

Thanks for the help so far, this is the best community on the net.

Update: I think I found a way to get my wireless working on this thread [http://ubuntuforums.org/showthread.php?t=1964200](http://ubuntuforums.org/showthread.php?t=1964200)
But I always get a little scared when it comes to this sort of thing so I could use a little backup.

---

### Post by oldfred on 2012-12-26
I do not know about wireless, mine has always just worked. Best to post a new thread on that issue with hardware version in title.

Usually you have to have the wired connection and then it will have an option to download a wireless driver.

Some have said wireless worked in BIOS install but not in UEFI, which to me is a bug somewhere. It then could be UEFI is not correctly telling the operating system what hardware as Ubuntu is the same in UEFI or BIOS and only grub is really different. But UEFI & BIOS write info to hard drive for operating systems to know what is where.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
[https://help.ubuntu.com/community/WifiDocs/](https://help.ubuntu.com/community/WifiDocs/)

Wireless script by anewguy
[http://ubuntuforums.org/showthread.php?t=2057034](http://ubuntuforums.org/showthread.php?t=2057034)

---

