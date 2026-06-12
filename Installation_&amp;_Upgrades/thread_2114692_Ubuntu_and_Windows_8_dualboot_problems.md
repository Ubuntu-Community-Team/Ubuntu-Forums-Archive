---
title: "Ubuntu and Windows 8 dualboot problems"
date: 2013-02-10
forum: Installation &amp; Upgrades
---

### Post by BebliucGeorge on 2013-02-10
Hello everyone,

This is my story. I have an Alienware m14x R1, with Windows 8 installed. Today I wanted to try Ubuntu ( not for my first time ), and Installed it, version 12.10 . The problem is that after I installed it ( made a different partition for it, and one for swap ), my Windows 8 install is not booting anymore. I can see it in the GRUB selection screen, but it gets stucked in the black background and blue logo screen. 

I tried using Repair-Boot, which added me a second Windows 8 option in the GRUB menu, but none of them seem to work.

This is my pastebin log: [http://paste.ubuntu.com/1634812/](http://paste.ubuntu.com/1634812/) 

Thanks in advance,
George

---

### Post by Bucky Ball on 2013-02-10
*Thread moved to **Installation & Upgrades**.*

---

### Post by oldfred on 2013-02-10
Welcome to the forums.

But this seems like a Windows issue. Did you shrink Windows using Windows own Disk tools? And reboot? Windows has to run chkdsk after any resize to update to its new size.

Also did you turn off fast boot in Windows 8 as it has hibernation on all the time to boot quickly and that can cause issues.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

    
It it this bug?
       Reboot/mount issues
[https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149)

    
       Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
BCDboot Command-Line Options Windows 8
[http://technet.microsoft.com/en-GB/library/hh824874.aspx](http://technet.microsoft.com/en-GB/library/hh824874.aspx)
BCD technical info Vista & efi
[http://technet.microsoft.com/en-us/library/cc721886%28v=ws.10%29.aspx]("http://technet.microsoft.com/en-us/library/cc721886%28v=ws.10%29.aspx")

[http://www.eightforums.com/](http://www.eightforums.com/)

---

