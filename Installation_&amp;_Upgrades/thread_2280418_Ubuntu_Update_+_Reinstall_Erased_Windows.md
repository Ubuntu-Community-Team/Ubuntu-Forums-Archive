---
title: "Ubuntu Update + Reinstall Erased Windows?"
date: 2015-05-30
forum: Installation &amp; Upgrades
---

### Post by ath-secondary on 2015-05-30
I had a laptop with Ubuntu 14.04 alongside Windows 8.1.

I heard about the new release for Ubuntu and wanted to upgrade my Ubuntu 14.04 to 15.04. Did the do-release-upgrade command, got an error midway through upgrade to 14.10. The version was recognized as 14.10 but many apps were corrupted, like all the system settings (could not view Software & Updates). The Grub Bootloader no longer showed my dual-boot options and just loaded Ubuntu so I couldn't go back to windows. It also couldn't show the normal Ubuntu either, saying something like a low-graphics mode (like [this]("http://1.bp.blogspot.com/-PnFRiv7-WQs/UL-oVayYxQI/AAAAAAAAAOM/webTu83iqdA/s629/error-1.png"), but I couldn't see the text)

This is where I decided to reinstall ubuntu 14.04 using the same USB I used to initially install it. I went through BIOS and got to boot through USB and installed Ubuntu 14.04. It asked to replace the current Ubuntu 14.10 version. After a successful install, update (from 14.04 to 14.10, then to 15.04) and reboot, the Grub still wasn't showing. I used [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") to reinstall the grub (pastebin [here]("http://paste.ubuntu.com/11445462/")), and that worked.

So on the renewed grub it no longer showed my Windows 8.1. Obviously I panicked and went through the BIOS again looking for boot options, and this time I saw a Windows Boot Manager. Selected it faster than lightning but was met with "failed to load image" messages that were shown on the screen for a very short time, then returned to the Grub menu. 

I went through so many askubuntu questions, ubuntuforum threads, youtube videos and websites in general to try and regain my Windows 8.1. I used TestDisk but it found no NTFS partitons:
**Disk /dev/sda **- 500GB
[LIST]
[*]EFI System 
[*]Unknown Type, only shows my Linux files when opened 
[*]Linux Swap 
[/LIST]
**Disk /dev/sdb **- 3995MB
[LIST]
[*]FAT32, with bad ending heads 
[/LIST]

I used [Foremost]("http://askubuntu.com/questions/3883/how-to-recover-deleted-files/3903#3903") to recover files from the /dev/sda disk and populated those into my /lost+found folder, which it actually found much of my Windows files, but it left me with no free diskspace while it was recovering and I had to search some more for ways to access the /lost+found folder since apparently it is hidden. None of the filenames were recognizable, and I had to delete the files in it to re-free the disk space.

So basically, a simple upgrade ended up breaking my Windows. The files are still there but I can't boot into the Windows and TestDisk can't detect the partition. I had a factory version of my Windows 8.1 on my Win7 desktop but apparently that was removed (even though I don't remember deleting it, it isn't appearing in the filesystem search). 

Is there any hope beyond buying a new Windows 8.1? Although there wasn't too much data on it that I also didn't have on my Windows 7 desktop, having Windows on my laptop is quite the necessity for Windows-only programs on the go.

---

### Post by Mark Phelps on 2015-05-31
> It asked to replace the current Ubuntu 14.10 version. This is not a "simple upgrade", as you thought, but instead, an offer to replace EVERYTHING on the drive -- which results in reformatting the drive, removing any existing Windows installation.  Unfortunately, it's not worded well and gives the impression that it's only going to replace Ubuntu -- which you found out, the hard way, is not what it does.

> Is there any hope beyond buying a new Windows 8.1? What MIGHT work is Windows partition recovery tools -- I would suggest using Active File Partition Recovery -- which is a Windows freeware partitioning tool.

If that doesn't work, you can also try Active File Recovery, which is free to try out, but requires a license to more than a test.  It's the best Windows data recovery tool I've seen.

---

### Post by oldfred on 2015-06-01
Which reinstall option did you choose. The only safe one is Something Else. Any auto reinstall does erase Windows and all recovery partitions.

 Reinstall says overwrite Ubuntu but it also erases existing Windows or any other partitions.
Sept 2014 Fix being released for one drive installs, but multiple drive installs must use Something Else. And fix is not in current versions released before Jan 2015.
this bug was fixed in the package ubiquity - 2.18.8.3 jan 2015
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

