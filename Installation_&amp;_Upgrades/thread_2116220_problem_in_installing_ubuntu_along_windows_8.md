---
title: "problem in installing ubuntu along windows 8"
date: 2013-02-15
forum: Installation &amp; Upgrades
---

### Post by hashexy on 2013-02-15
Hi all

I have HP-envy 23 that came with pre-installed windows 8. I disable the secure boot, make hardisk partitions, and made a liveUSB with ubuntu 12.10. 
when I boot the USB the grub menu come up with the following options: 
- try ubuntu without installing
- install ubuntu 
- install ubuntu for manufacturers
- check disk for errors. 

the problem is that whatever I choose a black screen comes and nothing happens. 

I tried every possible solution with "nomodeset" "vga" and every possible solution I could found on the forum with no change. 

Please Help!

---

### Post by oldfred on 2013-02-15
welcome to the forums.

With nVidia you have to have nomodeset. vga is obsolete. But some systems also required other settings in addition to nomodeset.
Some have needed these which you can try.
       vt.handoff=7 rootdelay=90 reboot=a,w

Are you booting in UEFI mode from UEFI menu or in BIOS/legacy/CSM mode?
Some new UEFI systems only boot in BIOS mode. But if possible you should boot in UEFI mode as then it installs in UEFI mode. But Boot-Repair will convert a BIOS install to UEFI.

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

    Have you backed up efi partition and the entire Windows partition?

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

    Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

    Different model HP
       HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)

    Older
       UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)

---

### Post by hashexy on 2013-02-16
Thanks a lot that help and now I can log in ubuntu. however, I can't boot into windows 8 right now. 


When I choose the second to last option (Windows 8 (loader) ) I get the following message: 

error: invalid EFI file path

i ran boot-repair and I got the following link if that helps

paste.ubuntu.com/1661325

please hlep

---

### Post by oldfred on 2013-02-16
The first two Windows entries were added by Boot-Repair and should work, the last two by os-prober which will not work. Since your system put all the recover loaders in the standard efi partition, Boot-Repair also added them to your grub menu.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by hashexy on 2013-02-16
thanks for the help
i did select window UEFI loader and windows 8 boots but i get a blue screen "your PC ran into a problem and it is going to restart." 
it also did windows repair and still not working. 

does this has to do with UEFI booting or is my windows corrupted. 
my latest URL from boot-repair is paste.ubuntu.com/1664295 if this will help. 


thanks a lot!

---

### Post by oldfred on 2013-02-16
If you are getting blue screen, grub has done its part to get you booting into Windows and it is a Windows issue.

Some of the Windows repairs have to be run multiple times. Did you run chkdsk as it has to run chkdsk after a resize.

---

