---
title: "writing a list of partitions"
date: 2011-11-18
forum: Installation &amp; Upgrades
---

### Post by nebu1a on 2011-11-18
i had to restore the grub menu, and i followed this guide (the comments are in italian, i'm sorry): [http://natonelbronx.wordpress.com/2008/03/03/ripristinare-grub-da-livecd-con-grub-install-e-altre-amenita/](http://natonelbronx.wordpress.com/2008/03/03/ripristinare-grub-da-livecd-con-grub-install-e-altre-amenita/)

when i gave *update-grub2* the ntfs partitions (with windows and datas) hadn't been found, instead i got the message:
> cannot find list of partitions! (try mounting /sys.)
this apart, the grub works well and i can launch it form the hs.

i tried to reinstall ubuntu, but not even in this way i can see any partion (the hd is a blank unallocated space in the installation procedure).
i see only a blank space with gparted too.
i tried to use * cfdisk /dev/sda*, but i got the error message:
> fatal error: bad primary partition 4: partition ends after end of the disk

i tried also testdisk, but then i had a windows message error at the startup (when i switch the pc on, not at the windows startup), that forces me to use a windows recovery disk. so i don't have the grub menu anymore and i have to install it from the live cd, etc, etc...

is there any way i can have a new partition list?

---

### Post by oldfred on 2011-11-19
If partition table has a bad entry then just about everything stops working as that is the first thing read.

First backup partition table entries to a file and store on another device.
sudo sfdisk -d /dev/sda > parts_sda.txt

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Also manual way, but fixparts above should be easier.
Use sfdisk to edit partitions and links to how to convert primary/logical
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
sfdisk to fix extended beyond end -partition outside the disk!
[http://ubuntuforums.org/showthread.php?t=1012825](http://ubuntuforums.org/showthread.php?t=1012825)

---

### Post by nebu1a on 2011-11-20
thank you oldfred, i launched fixparts and now all works fine.

---

### Post by oldfred on 2011-11-20
Glad that worked. You can changed thread to solved. See my signature.

---

### Post by nebu1a on 2011-11-20
> **oldfred said:**
>  See my signature.
i forgot...
bye

---

