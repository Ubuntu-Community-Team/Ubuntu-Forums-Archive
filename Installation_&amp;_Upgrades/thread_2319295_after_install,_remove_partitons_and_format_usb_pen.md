---
title: "after install, remove partitons and format usb pen drive"
date: 2016-04-02
forum: Installation &amp; Upgrades
---

### Post by dave-borkowskijr-z on 2016-04-02
I'm having problems removing the partitions so i can reformat my usb pen drive after using to install ubuntu.   Is there some sort of how to that anyone can point me to.  I can not seem to find one.

using "Disks" I get this output when i try to delete the partitions

Error deleting partition /dev/sdb2: Command-line `parted --script "/dev/sdb" "rm 2"' exited with non-zero exit status 1: Warning: /dev/sdb contains GPT signatures, indicating that it has a GPT table.  However, it does not have a valid fake msdos partition table, as it should.  Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables.  Or perhaps you deleted the GPT table, and are now using an msdos partition table.  Is this a GPT partition table?
Error: Both the primary and backup GPT tables are corrupt.  Try making a fresh table, and using Parted's rescue feature to recover partitions.
 (udisks-error-quark, 0)

under gparted i get this error
/dev/sdb contains GPT signatures, indicating that it has a GPT table.  However, it does not have a valid fake msdos partition table, as it should.  Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables.  Or perhaps you deleted the GPT table, and are now using an msdos partition table.  Is this a GPT partition table?


thank you

---

### Post by The Cog on 2016-04-02
This brute-force force will wipe the partition table completely by overwriting with zeros, leaving you free to re-partition with your chosen tool:
```
sudo dd if=/dev/zero of=/dev/sdb bs=1M count=1
```
Be **very** sure you get the right output device, not some internal disk drive! Recovery from an error will be very difficult.
After writing, I would remove and re-insert the stick.

---

### Post by oldfred on 2016-04-02
gpt also has a backup gpt partition table that is supposed to be at the end of drive.

And that is often the issue, as Windows tools convert gpt to MBR, but leave backup partition table.
Then Linux sees both MBR & gpt and assumes erasing & starting over is only choice.

Best to also see what fixparts says.
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sdb

---

### Post by sudodus on 2016-04-04
You can also use the [wipe menu of mkusb](https://help.ubuntu.com/community/mkusb/wipe), which wraps a safety belt around dd, so it is the same method under the hood as the one described by *The Cog*. In addition there are 'short-cuts' to standard partitioning schemes on top of wiping the first megabyte.

---

### Post by C.S.Cameron on 2016-04-04
Same thing happened to me a couple days ago.
To fix I recall using gparted, going to Device and then Create Partition Table.
Not exactly sure what I did in there, tried different things.
I eventually made a new FAT32 partition and tried installing 16.04 beta2.

---

