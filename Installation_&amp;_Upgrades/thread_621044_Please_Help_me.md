---
title: "Please Help me"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by kirtan on 2007-11-23
I installed Dual Boot Xp +Ubuntu 

Mean

I have Windows Xp in My sda1

and Ubuntu in sda7

Ubuntu Stops after Showing This information
[http://img440.imageshack.us/img440/8933/43062913sy6.jpg](http://img440.imageshack.us/img440/8933/43062913sy6.jpg)

i want to repair it or Remove Ubuntu and  format that Ubuntu partition but without affecting my old winXp installation 
plz tell me what to do ?:confused::(

plz help me I m in serious problem

---

### Post by banewman on 2007-11-23
The first thing I would do is boot from the live cd and open a terminal then type -
fsck -AV
which will check all filesystems and tell wht's going on. :)

---

### Post by kirtan on 2007-11-23
mean give you the out of that command ?:confused:

---

### Post by banewman on 2007-11-23
It will check the file systems and repair them and tell you what it is doing as it does it. :)

---

### Post by az on 2007-11-23
The disk probably has errors.  I would not use it unless you check it.

You can remove Ubuntu by simply fixing your MBR from windows.  That will reinstall the windows bootloader and you will no longer be able to boot into ubuntu.  If you want to reinstall Ubuntu, you can just start over on the existing Ubuntu partition.

I would suggest you check that partition for bad blocks first.  If you find any bad blocks, get another hard disk.

So, boot the live cd, open a terminal and run

sudo badblocks -v -s /dev/sda7

That will perform a read-only test on sda7

If there are no errors on the disk itself, try to fix the filesystem using fsck.  If you cannot recover the filesystem reinstall.  IF you want to recover files from the dammaged filesystem, use file-carving techniques, or try to force mount the partition and ignore errors.

help.ubuntu.com/community/DataRecovery

---

### Post by Sef on 2007-11-23
> I installed Dual Boot Xp +Ubuntu 

For Ubuntu, what file system did you use?

---

### Post by kirtan on 2007-11-23
i used ext3

---

### Post by kirtan on 2007-11-23
> **banewman said:**
> The first thing I would do is boot from the live cd and open a terminal then type -
fsck -AV
which will check all filesystems and tell wht's going on. :)

this is my result 

[http://img265.imageshack.us/img265/7278/23267397eh1.jpg](http://img265.imageshack.us/img265/7278/23267397eh1.jpg)

---

### Post by banewman on 2007-11-23
Nice camera work :)
Does it work better now?
If not we'll try next option. :)

---

### Post by kirtan on 2007-11-25
i formatted that partition but that also not worked .:(

reinstalled ubuntu but still not starting .

---

