---
title: "XP/XP/Ubuntu triple boot. Restore my MBR"
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by JohnJames86 on 2010-01-23
Hi,

I'm new to posting so I hope I haven't transgressed by starting new thread!!

I Have a dual boot XP/XP pc (don't ask why XP twice) and I have a USB Drive dual booting Mandriva and Ubuntu 9.  All worked well but I thought I'd look at Lynx 10.04 Alpha 2 and triple boot my USB drive.

During installation with the live CD the installation seemed to fail in the last section (probably just after the installation of the bootloader) though it appeared as just a stall.  I reran the installation but noticed the offer to update the installer, which I did.  Also we reached the stage where the boot loader was to be installed and I chose the MBR of the USB drive.

All was well with the reboot and the USB installations of Mnadriva Ubunto 9 and Ubuntu 10 all function. However, with the USB drive removed the windows machine would like to boot via a corrupted grub (probably the aborted first install of 10.04).

I would like to go back to my dual boot PC (from drive 0).  Would MBR fix make the first instance of XP the only recognised OS?.  What alternative is there to reinstate the XP/XP dual boot?

Sorry about the long post!

---

### Post by oldfred on 2010-01-23
It depends on what systems you have on what drives. I like to have the MBR of a drive boot to the operating system on that drive when you have more than one drive. I like grub so I make it the boot drive in BIOS and then choose other systems from the grub menu.

Windows normally installs additional windows to the first windows install with the boot flag set on. Then from that windows you boot the second windows. Grub cannot directly boot the second windows as files are moved to the first install. Not sure if this is true with XP/XP. There is a work around if you want to boot directly from grub by moving the boot flag before installing.

If you only have windows on the internal you can reinstall windows boot and it should see both. Your grub in the external should let you boot everything if the external is plugged in and it is set to boot first in BIOS. We have seen were grub2 installs to the internal. Not sure if it is/was a bug or if the user still had the internal drive set to boot first so grub auto installed to that drive.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you do not have a XP disk to reinstall the boot loader any windows disk prior to Vista will work. Also you can do this from Ubuntu.
Restore basic XP style boot loader
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Confirm that sda is the internal drive before running or change to correct drive.

---

### Post by JohnJames86 on 2010-01-23
@Oldfred

Thanks for quick response.

Quick rundown of my situation.

1.  I started with the PC dual boot to XPa and XPb ( I do a lot of video editing and use XPb a the editing install with minimal other software as Pinnacle tends to fall over with other software running)

2.  I've been interested in running Linux for some time now but decided this time to run from bootable USB HDD so I installed Ubuntu and Mandriva. With the USB plugged in I can boot any of the OS.  Without the USB Plugged in I revert to M$ XP OS only (XPa or XPb).  So far, so good.

3.  Tried to install 10.04 Alpha 2 in a new partition on USB HDD. Installation seemed to falter near to end - no offer of where to install boot loader.  Restarted installation, updated installer online and installed boot loader to USB HDD, rebooted all ok, can launch any OS from USB.

4.  Unplugged USB and booted PC but Grub starts but can't find drive (unplugged).  I expected normaldual boot menu for XP,XP but not grub..  This I assume came from aborted first install of 10.04.

From what you are saying do I understand that using that using MBR fix from my XP CD will reinstate the dual boot I had before or will it only see the single installation of Disk0 (C: Drive).  Will I have to re-install the second instance of XP?

---

### Post by oldfred on 2010-01-23
Windows combines boot files because it can only boot from a partition with the boot flag on. It adds an entry to boot.ini for the second windows. This is what you should have seen before? If booting windows from the external with grub it will give you a windows entry then from windows you should get another choice for which windows.

---

### Post by JohnJames86 on 2010-01-24
@oldfred

Thanks,

Case solved.  It was indeed simply a case of restoring the basic MBR.  I save the original boot.ini file by booting via the USB HDD then rebooting again to the restoration console and used FIXMBR.

Now I'm back to dual boot XP/XP from drive0 and multiboot from the USB HDD.

Read the threads you pointed out with interest.  Gives a good insight to problem solving but it would have been a sledge hammer and nut solution for my problem ... I was just a little shy of trying the simple solution in case I lost my second XP install!!

---

### Post by oldfred on 2010-01-24
Glad you got it working without much problem. 

One great thing about Linux is that, overtime people have created many tools for repairs of just about anything that can be repaired. Part of the problem is learning what tool is right to fix something we have managed to mess up. We will also spend days fixing things when you can reinstall in a half an hour or so.

If you want a lot of info about windows and multiple copies fo windows on a PC this site has lots of info. Based more on Vista but applies to windows in general also.

[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by JohnJames86 on 2010-01-24
@oldfred

I'll bear that in mind as I confess to using windows a lot for video work and will multiboot for some time yet.  I do like Ubuntu and the community at large seem very friendly and helpful.

I'll get back to trying 10.04 ... bearing in mind it simply goes and installs the bootloader without so much as a by your leave.  I'm used to being prompted that we've reached the bootloader stage and being able to choose from options.  Maybe it's a property of being an alpha version ... once bitten twice shy.

---

