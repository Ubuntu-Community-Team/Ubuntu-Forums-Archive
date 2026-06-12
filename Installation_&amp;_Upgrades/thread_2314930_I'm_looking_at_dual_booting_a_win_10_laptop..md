---
title: "I'm looking at dual booting a win 10 laptop."
date: 2016-02-24
forum: Installation &amp; Upgrades
---

### Post by l6griffin on 2016-02-24
I have an HP 15-G035WM laptop with win10 installed. I bought the laptop as a  mfg refurbished which may explain some ot settings I've found. I want to dual boot it with 14.04 LTS. I read the "UEFI Installing - Tips". 

My disk0 is setup with MBR, there are 3 volumes, C: 467MB, HP_TOOLS (D:)8192MB, and System Reserved. I cleaned out all the old files, delete the 8GB d: partition. Then extended C: to get the 8GB from D:. Then shrunk C: down to 205GB, the best I could do. Then created a new D: of 227GB. I then tried to download the UEFI install file at, [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download), and got the error page not found. The BIOS appears to be set for legacy and I would prefer no UEFI. According to the BIOS the OS was non-Windows, Visualization Technology disabled, legacy support enabled, secured boot disabled. When I booted the 14.04 LTS ISO on DVD and trial ran install it did not see the volumes.  It saw the /dev/sda 500107 MB free. Is there another flavor I should use?

---

### Post by yancek on 2016-02-24
The Ubuntu download page at the link below.

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

If your windows 10 is actually installed MBR, then you need to make sure you boot the Ubuntu install medium that way.  If you install Ubuntu UEFI and windows is MBR, windows won't boot.  You can't mix the two.  See the link below for a brief explanation.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

There really isn't much point in creating a partition on windows on which to install Linux because windows is not capable of creating a Linux filesystem so you will have to do that during the installation anyway.  Take a look at the site below for a detailed tutorial on dual booting windows/Ubuntu using MBR.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by l6griffin on 2016-02-24
I've found the download page a few times, that's where I got the ISO to the trial install with mention above.

I'm trying to ignore UEFI, one of the reasons I bought this laptop was legacy mode. :)

Don't know of a hand book for linux with all the little commands like chmod, ls, lsmod, lsusb listed by function.

No idea why the install doesn't my NTFS partitions.

---

### Post by oldfred on 2016-02-25
Even Windows 8 or 10 in BIOS mode need fast start up off. That is always on hibernation which prevents Linux from seeing partition.
       Fast Startup off
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

Did you use Windows to convert from gpt to MBR? Windows does not do it correctly and you have to run fixparts to repair it.
Post this:
sudo parted -l
sudo fdisk -lu

---

### Post by l6griffin on 2016-02-26
oldfred glad you caught this. The BIOS and partition tables were as I found them. A light went on (DUH) and booted ubuntu from the DVD/ISO and ran gparted, surprise GPT table is corrupted. I bought the laptop from newegg as refurbished. The ad for the laptop had the HP logo and info for the model. I called customer service at newegg and tried to explain to the lady on the phone that there was a problem, 90 day warranty - no refunds, unless out of stock which it is. I was told that they sent out to someone for refurb. I'm not sure what I want to do, hassle the return and hope for a refund or backup win10, low level format the HD, partition, and restore win10.

---

### Post by oldfred on 2016-02-26
If system was UEFI/gpt and tech just reinstalled in BIOS mode, then drive was converted by Windows from gpt to MBR as Windows has to have MBR for BIOS boot.
But Windows has had a bug for years on any install of BIOS boot mode over a gpt drive does not remove the backup gpt partition table.
You can remove backup partition table.
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda

If you want UEFI/gpt, then you have to totally reinstall Windows. Windows has the OEM license key in UEFI, but you have to install OEM or HP copy not just any generic copy. Not sure if then whoever refurbed it just installed a BIOS version they had laying around, not the original HP OEM version that should be installed and in UEFI mode.

I would do a full backup of what system is now, so you could get back before trying other things.
      
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Not sure if this would work for you or not. Either way Windows is going to want to update to Windows 10.
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

You can stay with BIOS/MBR or totally reinstall, your choice. May be a bit easier to stay BIOS.
HP also needs a work around to boot anything but Windows in UEFI mode, but that is fix that every HP, so far, has needed and seems to work.

Minor advantages to UEFI/gpt, but may not worth hassle to convert.
      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by l6griffin on 2016-02-26
It does not get better. I first tried to copy the system image and that couldn't be done to a DVD. I looked for other options and ran into more errors, one from a win7 program that should not even be there. I'll see if I can get a refund or move to a ubuntu machine. Thanks oldfred your posts are always appreciated.

---

