---
title: "triple boot"
date: 2013-02-20
forum: Installation &amp; Upgrades
---

### Post by bkunsada on 2013-02-20
Hi,

My HDD has four partitions:
[LIST]
[*]WIn XP [primary] C: 23GB
[*]Empty [Primary] F: 15GB
[*]Win 7 [logical] D: 39GB
[*]Empty [logical] E: 219GB
[/LIST]

I want to install ubuntu alongside XP & 7. Using Ubuntu's "something else" option I found that ubuntu detected my HDD and all of its four partitions.

My question: should I choose SDA6 [empty [logical E: 219GB] for ubuntu's boot loader or should I choose something else.

NB: SDA1 contains XP & SDA5 contains win 7. 

Thanks in advance, IMT

---

### Post by ahallubuntu on 2013-02-20
~

---

### Post by bkunsada on 2013-02-20
MY XP is installed on a primary partition (dev/SDA1)while win 7 is on logical partition (dev/SDA5).
UNder this dual boot configuration, my boot loader is on C:/ [win XP's directory].

Ubuntu's install option page only gave me three choices, install ubuntu and erase windows 7, install ubuntu alongside windows 7, and something else.

If I choose to install ubuntu's boot loader on DEV/SDA will my XP still be detected by ubuntu?

I want to install ubuntu on my largest partition (E: 219 GB logical partition - dev/sda6). So, I should clarify ubuntu not to use other partition except dev/sda6, right?!

---

### Post by oldfred on 2013-02-22
Ubuntu will not install to NTFS partitions.

If you just want the default install of / (root) and swap just delete the empty NTFS partition (make sure it is empty) and install into the unallocated space. Backups and a Windows repairCD are highly suggested. Most times it works without issues, but the one time you do not make backups is the time it does not.

If you want more control, you have to use Something Else and manually specify partitions. You then can add /home if you want and choose to install the grub2 boot loader to sda.

Since Windows 7 is in a logical partition it will always have to boot from the XP partition. Windows only boots from primary partitions. All of Windows 7 boot files are in the XP partition. So grub will show the Windows as a boot option and then from Windows still should get the option on which Windows to boot.

       To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
    
       Install options, Do not use erase entire drive unless that is really what you want.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

