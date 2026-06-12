---
title: "Triple boot WinXP, Windows 8 and Ubuntu"
date: 2012-12-19
forum: Installation &amp; Upgrades
---

### Post by glock356 on 2012-12-19
Hello!

I have installed on dual boot WinXP and Windows 8, XP installed first.
I want to install Ubuntu on this computer to triple boot - is this possible?
Where to install bootloader for Ubuntu?

I am insttaled Ubuntu on dual boot with XP, W7 and W8, never on triple boot - i need XP for some apps which is not worked on W8.

---

### Post by Ozymandias_117 on 2012-12-19
Yes, this is possible.  As to the where to install the bootloader, if you're using BIOS, then it has to be installed the same as for a dual boot.  If you're using UEFI then you will need to put it into your current UEFI boot partition.

---

### Post by oldfred on 2012-12-19
Unless you installed the Windows separately you will only get one entry in grub2's menu. As your second install of Windows puts its boot files in the first install's partition or the active or boot flagged partition.

       To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
    
What is your current partition layout. You will need an extended partition so you can make several logical partitions for Ubuntu.

From liveCD post this.
       sudo parted /dev/sda unit s print
    
You should also plan a shared NTFS data partition, but still may need to turn off the auto hibernation of Windows 8 (that makes it boot quickly.)

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

