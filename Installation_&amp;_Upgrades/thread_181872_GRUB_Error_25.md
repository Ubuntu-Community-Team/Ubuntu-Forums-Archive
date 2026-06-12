---
title: "GRUB Error 25"
date: 2006-05-24
forum: Installation &amp; Upgrades
---

### Post by aball65 on 2006-05-24
Ubuntu v5.10 installed like a charm on a new USP external 80GB drive.  Kudos to the Ubuntu installation team. :)   However, the install has turned my computer into an expensive nite lite. ](*,)   I get the following error message when rebooting:

GRUB Loading Stage1.5.

GRUB Loading, Please Wait...
Error 25

I was able to retore my master boot record and came straight here for enlightenment.  Any ideas would be greatly appreciated.

Thanks a ton.

---

### Post by Sef on 2006-05-24
> 25 : Disk read error
    This error is returned if there is a disk read error when trying to probe or read data from a particular disk.

How did you set it to boot up?  From the external disk or your hard disk?

---

### Post by aball65 on 2006-05-24
From the hard disk - the same disk xp is on.

---

### Post by confused57 on 2006-05-25
Maybe there's something in this thread that will help:

[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)

---

### Post by Sef on 2006-05-25
> From the hard disk - the same disk xp is on.

Is the XP partition the boot partition?

---

### Post by nalmeth on 2006-05-25
I don't know what Error 25 is specifically, but here's a link to restore GRUB:
[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

Just be careful around your NTFS as you usually would. This involves using the install CD, skipping installation, and installing grub.

---

