---
title: "Can't Remove Ubuntu and Restore Windows!"
date: 2010-07-01
forum: Installation &amp; Upgrades
---

### Post by RTFR on 2010-07-01
I have been dealing with this all day! I cannot remove Ubuntu and recover the free space for Windows. When I remove Ubuntu, I can't access Windows. 
 
I have three partitions, one being the main Windows partition and two with no names being the ubuntu partitions.
 
Please help. I like Ubuntu, but I wish to revert to Windows. Thanks.

---

### Post by darkod on 2010-07-01
Did you use your windows cd/dvd to reinstall the windows bootloader to the MBR of the disk?
Instructions how to reinstall various bootloaders here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

In case you don't have windows cd, another quick procedure is using the ubuntu cd in live mode. In terminal just execute:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Note: if the disk is not /dev/sda but another, replace accordingly in the second command.

After the first command there will be some warnings which will sound scary, ignore them. You will not be using lilo at all, just ignore them. As soon as the command prompt appears again, just run the second command.

Restart without the cd and you should see windows boot directly.

---

### Post by RTFR on 2010-07-01
Thanks. Should I try that before or after trying to delete the partitions in Windows?

---

### Post by darkod on 2010-07-02
Doesn't really matter but I would prefer to get windows booting first with its bootloader, and only then delete the partition using windows Disk Management.

You can delete them first, but then you can't boot anything except the ubuntu cd in live mode, or the windows cd to repair the bootloader.

It should work either way.

---

