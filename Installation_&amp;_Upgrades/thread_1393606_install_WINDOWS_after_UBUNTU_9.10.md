---
title: "install WINDOWS after UBUNTU 9.10"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by mrcool123 on 2010-01-29
I have ubuntu 9.10.  I would like to install windows on a different partition on my hard drive.  I am looking for a step by step guide to what I need to do if I have a windows install CD.  I am not linux savvy and this guide does not give me any idea where to start:

thanks

"
Normally when Windows is installed after Ubuntu the master boot record will be overwritten. This means that you would have to boot off a LiveCD and re-install grub. However, here is an alternative method: 

[LIST=1]
[*]Create an NTFS partition for windows (using fdisk or whatever tool you are familiar with)
[*]Backup the boot sector e.g. dd if=/dev/hda of=/mbr.bin bs=512 count=1
[*]Install windows
[*]Boot into a LiveCD
[*]Mount your root partition in the LiveCD
[*]Restore the boot sector e.g. dd if=/media/hda/mbr.bin of=/dev/hda bs=512 count=1
[*]Restart and Ubuntu will boot
[*]Setup grub to boot windows"
[/LIST]

---

### Post by mr clark25 on 2010-01-29
i just did the same thing. here is my thread:

[http://ubuntuforums.org/showthread.php?t=1388222](http://ubuntuforums.org/showthread.php?t=1388222)

which bersion of windows do you plan to install?

---

### Post by presence1960 on 2010-01-29
> **mr clark25 said:**
> i just did the same thing. here is my thread:

[http://ubuntuforums.org/showthread.php?t=1388222](http://ubuntuforums.org/showthread.php?t=1388222)

which bersion of windows do you plan to install?

Mr Clark can definitely help you with this one.

---

