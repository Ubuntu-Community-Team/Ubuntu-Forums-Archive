---
title: "Multiboot Setup for Raid-0 Array?"
date: 2012-08-01
forum: Installation &amp; Upgrades
---

### Post by stev067 on 2012-08-01
Greetings!

I would like to set up a multiboot environment with the following operating systems striped on my dual SSD mobo-array:

windows 7
windows 8
ubuntu 12.04

I have a 1TB spindle drive that will be dedicated to OS backups, and a 3TB spindle drive where I will store all of my documents and media.

Will I be able to do this?
Is there a certain order I should install them in?
Any other advice/concerns, vague or detailed step-by-step will be greatly appreciated.

Thanks!

---

### Post by oldfred on 2012-08-01
I do not know RAID.

But you have to use gpt with drives over 2TB and Windows only boots from gpt drives with UEFI.

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

While Vista, it still is how Windows works:
To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by stev067 on 2012-08-02
Thank you for your reply! Last night, I made it pretty far. I had windows 7 installed on a partition, and ubuntu installed on another (both striped on the SSDs). I failed at setting up GRUB and windows boot manager, and ended up messing up a boot flag and had to do a windows restore. Going to try again tonight using alternate ubuntu.

---

### Post by stev067 on 2012-08-03
Please someone help me finish the job! I have ubuntu and windows 7 installed. Grub2 will open ubuntu, but when I try to open windows 7, it says "BOOTMGR image is corrupt." Boot-repair doesn't fix it, and I'm afraid to try windows repair. Anybody?

[http://paste.ubuntu.com/1127299/](http://paste.ubuntu.com/1127299/)

---

### Post by stev067 on 2012-08-03
Fixed it! These instructions helped:

[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)

---

