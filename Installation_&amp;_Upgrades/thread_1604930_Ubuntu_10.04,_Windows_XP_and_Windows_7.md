---
title: "Ubuntu 10.04, Windows XP and Windows 7"
date: 2010-10-24
forum: Installation &amp; Upgrades
---

### Post by acompay on 2010-10-24
Hello There,
I have Ubuntu 10.04 and Windows XP running each one in a partition of two different hard drives. I want to install Windows 7 in a second partition of the hard drive where Ubuntu is running. Windows 7 did not see the hard drive where Ubuntu is running. So I understand that I need to format the partition where Ubuntu is running, install Windows 7 and later on Ubuntu 10.04 which will create the boot for the three systems. But I want to backup Ubuntu's installation, and after installing Windows 7, install the backup. So I will need to add the file for the dual booting. How can I do it? Is it there any piece of software that could create the three booting option that I need?
I would appreciate very much your help!
Regards,

---

### Post by oldfred on 2010-10-24
Windows does not see linux partitions. But if you shrink your Ubuntu install and have free space or create a NTFS partition windows should then see the space or partition and let you install.

You do have to make sure the NTFS partition is a primary partition or have available another primary partition with the free space.

Windows likes to combine boot loaders into one as that is the only way windows boots. But then you cannot directly boot from grub2. You boot the first windows and then choose the second. With two drives it may be best to unplug the other if you want to directly boot with grub.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

