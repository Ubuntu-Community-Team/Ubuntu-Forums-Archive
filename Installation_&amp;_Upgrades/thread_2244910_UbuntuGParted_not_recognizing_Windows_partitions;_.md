---
title: "Ubuntu/GParted not recognizing Windows partitions; FixParts doesn't work"
date: 2014-09-19
forum: Installation &amp; Upgrades
---

### Post by dennis31 on 2014-09-19
Hello everyone,

All the previous issues I had have been resolved. (My old thread: [http://ubuntuforums.org/showthread.php?t=2241011](http://ubuntuforums.org/showthread.php?t=2241011).)

I have deleted my RAID sets and all logical partitions, then I re-installed Windows. The HDD on which it is located now only contains 3 primary partitions for Windows and some 60 GB unallocated space where I want to install Ubuntu. (These partitions were made by Windows during installation, but I did some resizing in Windows afterwards.) No RAID or logical partitions this time.

Now when trying to install Ubuntu or running GParted it does not recognize my Windows partitions. I did some searching and found this thread with the solution: [http://ubuntuforums.org/showthread.php?t=2206142](http://ubuntuforums.org/showthread.php?t=2206142). After reading the provided link ([http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)) I suspected I still have old GPT and/or old RAID data on (some of) my disk(s). (Note: when running Ubuntu from USB it does recognize my Windows partitions, but the installer does not.)

So I tried to use FixParts ([http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)), but Ubuntu warned me the package was not well-formed. I tried to install it anyway, but that did not work. Then I re-booted in Windows and ran the Windows version, which didn't work either. (I get an error message saying MSVCP100.dll is missing.)

Next I downloaded SystemRescueCD -because it includes GPT fdisk and FixParts- and booted it from USB. Then I got an error saying it can't find a keyboard. I let the menu time out so eventually it did boot (the first option in the SystemRescueCD menu), but I still can't use my keyboard. Other times when booting from USB my keyboard works fine.

Does anyone here have any ideas on how to fix this problem? Thanks in advance for the help.

Dennis

---

### Post by oldfred on 2014-09-19
I have not had issues with fixparts, but have not yet installed it to 14.04.

But if drive was RAID and not gpt then you may only need to remove RAID meta-data.

       Even if raid not used BIOS may have set parameters, Also check BIOS settings
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Run chkdsk on any NTFS partitions even if they currently work.
Most of reasons for installer not showing Windows, any partition type error

Post this also:
sudo parted -l
sudo fdisk -lu
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

---

