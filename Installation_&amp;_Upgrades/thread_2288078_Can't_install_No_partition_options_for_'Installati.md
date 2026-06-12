---
title: "Can't install: No partition options for 'Installation type'"
date: 2015-07-24
forum: Installation &amp; Upgrades
---

### Post by jared30 on 2015-07-24
Hi there!

I followed a bunch of online tutorials and created a 20 GB partition, created a bootable USB with Ubuntu 14.04, disabled secure boot, disabled acceleration for Intel Rapid Storage Technology, tried so many suggestions online about how to fix this problem but nothing is working.

The problem is that when I dual boot (I have Windows 8.1) and select Ubuntu OS, I click "Try Ubuntu without installing" and when I get the 'Installation Type' part of the installer, no partitions shows up and when I click the "+" symbol, it freezes and does nothing.

My computer specs: [http://oi58.tinypic.com/3304chi.jpg](http://oi58.tinypic.com/3304chi.jpg)

What the problem is: [http://oi57.tinypic.com/jrw6rp.jpg](http://oi57.tinypic.com/jrw6rp.jpg)

I really need Ubuntu Linux for my engineering paper and all I want to do is install it :( any help is greatly appreciated!

---

### Post by yancek on 2015-07-24
The first "Installation Type" window should give you several options, Install Alongside, Erase Disk and the one you want is "Something Else".  Try that and see if any change if you haven't.  Have you tried the flash drive on another computer to see if it works?  Since you have windows 8, it probably uses UEFI to boot so you need to select that option in Ubuntu.

---

### Post by jared30 on 2015-07-24
The problem is that I don't have that first 'Installation Type' window. When I boot via my USB it boots up in UEFI and gives me a black screen saying 'Try Ubuntu without installing', 'Install Ubuntu', 'Scan for Repairs' etc.

I tried it on my brother's laptop and it worked fine, just not on mine...He has a Dell Inspiron just like mine which is weird.

---

### Post by grahammechanical on 2015-07-24
The Try Ubuntu option should not give you an Installation Type dialog. We should only get that when we click Install Ubuntu. The Try Ubuntu option should load to a working desktop environment. From there we can run an application called Gparted that will examine the hard disk and show what partitions are on it. It does other stuff as well. A screen shot of what Gparted is showing would be useful.

I think that you are seeing the Advanced Options Welcome page. The usual process once the computer starts to load from the live session is to see a purple screen with an icons of a keyboard and a human at the the bottom of the screen. If we press Enter at that point and we get another screen where we can select the language (default English). The underlying screen has these options.

Try Ubuntu without installing
Install Ubuntu
check disc for defects
Test memory
Boot from first hard disk

If at this screen we press F6 a small menu will appear and in the list will be nomodest. Select that, press Enter and then Esc to get back to the underlying screen and then select Try Ubuntu. It should load to a desktop with an icon labelled Install Ubuntu.

See section 6 - F6

Manufacturers do vary the hardware in their machines.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Regards.

---

### Post by oldfred on 2015-07-24
Depending on whether you boot in UEFI or BIOS/CSM/Legacy boot mode, you get different screens.
And how you boot installer from UEFI boot menu, UEFI or BIOS it then how it installs. You really want UEFI if Windows is UEFI.
       You will need to use the 64 bit version of 14.04 or 15.04 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need Windows  fast start up (hibernation) and UEFI/BIOS fast boot quick boot UEFI settings. Vital for some systems. 
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive. Reboot after shrink so it can run its repairs to its new size.
Make sure fast startup is off in Windows. That always on hibernation prevents Linux NTFS driver from seeing the Windows install.
Backup efi(ESP) partition and Windows partition before Install of Ubuntu. Only one efi partition per hard drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

