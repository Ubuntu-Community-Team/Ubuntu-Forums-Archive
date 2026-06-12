---
title: "usb-installer missing in 10.04LTS Release"
date: 2010-12-26
forum: Installation &amp; Upgrades
---

### Post by dlpenguinlover on 2010-12-26
Hi. I just bought a USB Hard Drive to install ubuntu to show friends. I was able to boot the Live CD but I noticed the option to install to USB was missing. I believe I last saw this in 8.10. So, I went searching the forums for solutions but all I found was the Windows Executable "usb-installer.exe" . So, I try to look for this, its not there. Does anyone know what I need to do to do this? I'm going to be using this as a portable install across lots of different computers, Does this make a difference?

Thanks.

---

### Post by Herman on 2010-12-26
GNU/Linux distributions are not encumbered by restrictive license  agreements that  bind them to any particular hardware so it seems like  quite a novelty to most people that Ubuntu can boot and run in just  about any computer  without too many problems. 
In fact Ubuntu goes quite out of its way to try to make itself able to  configure itself automatically at boot time for just about any kind of  hardware, and it does a darned good job of that too.

No special options are required at installation time.  I have Ubuntu installed all kinds of ways in all kinds of disks.

When installing Ubuntu in a drive you think you might want to remove and use as a portable drive, you just need to make sure you install GRUB to MBR in the same drive Ubuntu is installed in.
You may need to follow some kind of an installation guide if you're not sure how to do that.

USB drives are more likely to be used as 'removable' drives than other kinds of drives, but I sometimes also unplug IDE and SATA drives containing Ubuntu and plug them into different computers. They boot and run just the same, regardless of whether they happen to be connected by IDE, SATA or USB cables. 

If the computer you want to boot your removable drive in doesn't have GRUB, you may need to boot from the BIOS boot menu, press F8 or F12 or some other key at boot time for that, it depends on the make and model of the motherboard. Some computers can't boot a USB drive at all.

When special graphics card drivers are required for running graphics intensive applications like google earth or the like, it's easy to use the 'System', 'Administration','Hardware Drivers' function. You may find it expedient to uninstall those special drivers when you're finished to make it easier to boot the desktop if you're planning to boot in some other computer next time.

Other than that I find that Ubuntu can easily boot and run in just about any computer I've tried it in. :)

---

### Post by mikewhatever on 2010-12-26
The Startup Disk Creator is under System->Administration, and it is available in 10.04.

---

### Post by C.S.Cameron on 2010-12-26
You could also try UNetbootin if usb-creator has problems.

---

### Post by dlpenguinlover on 2010-12-26
In 10.04.1 , its not there..........

---

### Post by efflandt on 2010-12-26
Startup Disk Creator is for putting a bootable live/install iso on a USB FAT32 partition.  Maybe that does not appear if you do not have USB attached with FAT32 (what format is the partition on your USB?).

If you have a USB hard drive, I would just partition it how you want it for Linux (and maybe also an NTFS partition if you also want to use part of it for Windows).  Then do a regular Ubuntu install.

But during **10.04** or earlier install you have to pay attention to the summary screen after you configure your username/password and use the **Advanced** button to tell it to put grub on /dev/sdb or whatever your USB hd is.

That is changed in 10.10 or later install, where location for grub is selected at bottom of manual partitioning screen.

I have done that with several WD Passport USB hard drives, and did a regular install to 8 GB USB flash to try Kubuntu Natty development.  Or when I got an SSD drive, I initially used it as an internal drive my laptop to install Ubuntu 10.10 on it with default video drivers, and it worked fine when I moved that SSD to my desktop as internal drive.

---

### Post by mikewhatever on 2010-12-26
> **dlpenguinlover said:**
> In 10.04.1 , its not there..........

Interesting. Let's see if the packages are installed. Run the command below:
```
dpkg -l | grep usb-creator
```

If the output shows usb-creator-common and usb-creator-gtk, try launching the program with the **usb-creator-gtk** command.
If everything works, edit the menu and add usb-creator-gtk manually. If not, then the program is not installed, and you'll need to install the two packages.

---

