---
title: "Need help ASAP! (dual-boot)"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by bj0rn on 2006-06-11
I'm just about to install Ubuntu and I have a very important question. I know that dual-boot users should have 3 partitions overall - the ntfs/fat32 where Windows is installed, a linux-swap partition and an ext3 partition.

How am I supposed to mark the ntfs/fat32 partition on the installer? /boot?

---

### Post by jeremytaylor on 2006-06-11
No! leave it unmounted. Or if you want to acess it then call it something harmless like /media/windows.
Jeremy

---

### Post by The last Bert on 2006-06-11
Well, I have a seperate hard drive with my linux install. I created a boot partition (/boot), a swap partition and a root partition(/) on that hard drive. The installer should detect your ntfs/fat partitions and should leave them alone. It will detect your windows install, and make it an option in grub at startup.

Not sure if thats the answer you wanted, but i think it should help.

---

### Post by confused57 on 2006-06-11
First of all, run the LiveCD(if you haven't already) just to see if it works on your system.

Here's 2 excellent dualboot guides:

[http://psychocats.net/ubuntu/windowstoubuntu.html](http://psychocats.net/ubuntu/windowstoubuntu.html)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Be sure to defrag your Windows partition before installing Ubuntu.  The Ubuntu installer will give you the option of resizing your Windows partition and install Ubuntu on the remaining "free space"...the default installation will install a root(/) partition and a swap partition(usually 1.5x the size of your ram).  The grub bootloader will install on the Windows mbr, where you'll have the option of booting Windows or Ubuntu during bootup.

---

