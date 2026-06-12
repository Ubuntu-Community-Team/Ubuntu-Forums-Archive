---
title: "Setting Grub location"
date: 2015-08-28
forum: Installation &amp; Upgrades
---

### Post by tig2 on 2015-08-28
Hello all,

I was checking recently several Linux distributions  (all of them are based on Ubuntu) and installed them on my external USB  hard drive. In order to prevent any accidental problems with my internal  HD MBR, I removed the internal hard drive completely from my laptop and  during installation used option "install bootloader to /sda" (since  external drive just became /sda) just to make external USB drive easily  bootable. I used  this option to install bootloader to /sda for all  Linux systems, since I wanted to see how different grubs look and  function. Then I made a choice and settled on a particular Grub2 related  to a particular Linux distro installed on /sda7 and made some  adjustments in its configuration file.

Everything was fine until I  had a large update of a Linux distro installed on /sda8. It added some  new kernels, which apparently forced it to reinstall its Grub. And this  Grub was installed in /sda knocking out my selected and customised  Grub2, which I liked and chose before. So, here is what I need to  resolve:

1) I need to make certain that all but one distros  either do not install their grub completely during major updates, or  install them into their own root partition, where they will not bother  anybody. All settings in the system pointing to Grub location should be  permanently adjusted.

2) What really worries me is that after I  put back my internal HD, it will become /sda, and the external USB drive  with all those Linux distros will be /sdb. Will those major Linux  updates with grub re-install try to install it in my internal HD /sda  and knock out my Windows MBR? I really don't want that to happen. And  even if I manage to point the grub installation for all of them into  their own root partition, there will still be one that boots the entire  external drive. Will that Linux distro that produced it (in my case its  system is on /sda7) be trying to install it in /sda, which is now  internal HD, or will correct itself and install it in /sdb? How to make  sure that the problem of replacing Windows MBR does not occur?

I  would really appreciate the answer to these questions. I am just  learning Linux system, so the detailed command lines for the terminal  would be much greater help than just general strategic approach.

Thank you.

Tig.

---

### Post by oldfred on 2015-08-28
Grub/Ubuntu now use UUID, so change from sda to sdb almost always works.

       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short 

One user changed this to no choice and it worked. Others install to a partition as long as you have one install still in MBR.

 #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

Best to document system with either bootinfo script or Boot-Repair's summary report. bootinfoscript is first part of Summary report.
      
 [URL="https://help.ubuntu.com/community/Boot-Info"]https://help.ubuntu.com/community/Boot-Info

[/URL]
 [URL="https://github.com/arvidjaar/bootinfoscript"]https://github.com/arvidjaar/bootinfoscript

[/URL]
 Updated fork  as bootinfoscript does not seem to be maintained
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript)
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/latest/download](http://sourceforge.net/projects/bootinfoscript/files/latest/download)

[URL="https://github.com/arvidjaar/bootinfoscript"]
[/URL] 

[URL="https://help.ubuntu.com/community/Boot-Info"]
[/URL]

---

### Post by tig2 on 2015-08-28
Thank you for your reply!

I don't know how I missed that thread when I was searching forums: [http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

It appears that I have successfully changed the grub location for all (except one) Linux systems to their local partitions. I hope it will stay this way for many updates to come. It also looks like the grub location is linked to the disk ID rather than /sda, as you said. Well, I guess I will see later if it is a guaranteed scenario.

Tig.

---

### Post by Dennis N on 2015-08-28
Another practice that can be used is to prevent the grub packages from upgrading unless they are for the OS which provides the grub menu. The dpkg command has an option to do this. Also, Synaptic Package Manager can lock the grub packages to their current version. It saves you the need to reinstall grub.

Also, update-grub does not reinstall grub when you have a kernel upgrade - it just creates a new grub.cfg file.

---

### Post by efflandt on 2015-08-29
I know that you **cannot** put grub boot loader on a logical partition, but I know that you can put it in an msdos primary partition and think you might be able to put it on an extended partition itself (one of the first 4 partitions). Many years ago while still using LILO with standard DOS/WIN mbr I put LILO on an extended partition.

My current desktop PC has standard mbr on sda because early into grub2 some Windows programs would store data in what they "thought" was an unused part of the mbr which would mess up grub. So I changed that back to standard mbr by using dd to write /usr/lib/syslinux/mbr.bin to the mbr. I don't have swap. I have 14.04 grub on its sda4, but usually boot everything from 12.04's grub on sdb (SSD). In a pinch I can set the boot flag on sda4 (instead of Windows) and boot sda if something happens to sdb.

My MSI laptop with Win7 kept doing something odd when I installed 13.10 (when it was still current) with grub on sda4. If I cleared the boot flag on sda2 and set it to sda4, something kept resetting the boot flag on sda2, so it would only boot Windows. So I had to put grub on a USB stick and use that when I wanted to boot Linux. But I have since installed 14.04 to mSATA SSD card and set that as boot device. That worked even while I had its hard drive removed to malware/virus scan it from another computer (I accidentally installed Binkiland browser in Win7 with adware/malware from a bogus website when looking for Google Chrome). When Win7 had an update that would only work when it booted from standard mbr, I temporarily booted sda.

---

### Post by yancek on 2015-08-29
> I know that you **cannot** put grub boot loader on a logical partition 

I'd have to disagree with that.  My primary system which I use to boot the various installations is on a logical partition (sda8) with Grub boot code in the master boot record pointing to that partition and am able to boot it as well as the various other distributions I have installed.    

> you might be able to put it on an extended partition itself

I'm not sure I'm reading your intention correctly as an Extended partition (which needs to be a primary partition) is simply a container for logical partitions and cannot hold data, logical partitions can.  With regard to the boot flag being set, that is windows specific and a partition needs to be marked active to boot windows.  In addition, windows boot files need to be on a primary partition.  Neither is necessary with Linux.

---

