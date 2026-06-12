---
title: "Switching a RAID5 3-disk array on/off during booting"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by xenophon on 2006-11-01
Hi, and greetings from Athens.

I've managed to install a RAID-5 array of three SATA disks [Intel 915GEV motherboard, DawiControl-4300 controller], that appears as an ext3 volume on the desktop. Here's the relevant entry from my /etc/fstab -

/dev/md0        /mnt/depot      ext3    rw,auto,user    0   1

All is well, and configuring the md0 volume was not as painful as I expected;) , but I have a question to ask:

Sometimes I would rather leave the disk array OFF, since I don't need it except for network backups. That also eliminates the noise and the heat from the disks.

When I do that, my Ubuntu 6.06 machine exits to a root shell during booting, apparently because it could not identify the /dev/md0 device. I can continue booting by pressing control-D, and there appear to be no further complications.

Still, I wonder whether some sort of fstab modification would prevent this from happening.

TIA

Xen

---

### Post by wkulecz on 2006-11-01
try changing rw,auto,user 0 1 to rw,noauto,user 1 2

hth,
--wally.

---

### Post by xenophon on 2006-11-01
Thanks, I'll try that. BTW, what do these numbers mean?

---

### Post by wkulecz on 2006-11-02
The numbers are the "dump" level and "pass" number.  The dump level can be ignored unless you use the old dump utility or somthing like it for backup.
Pass number controls when or if fsck is run.

from "man fstab":
 The fifth field, (fs_freq), is used for these filesystems by the dump
 command to determine which filesystems need to be dumped.  If the  fifth
 field  is  not present, a value of zero is returned and dump will assume
 that the filesystem does not need to be dumped.

The sixth field, (fs_passno), is used by the fsck program  to  determine 
the order in which filesystem checks are done at reboot time.  The
root filesystem should be specified with a fs_passno  of  1,  and  other
filesystems  should  have  a fs_passno of 2.  Filesystems within a drive
will be checked sequentially, but filesystems on different  drives  will
be  checked  at  the  same  time to utilize parallelism available in the
hardware.  If the sixth field is not present or zero, a value of zero is
returned  and  fsck  will assume that the filesystem does not need to be
checked.

If the array is powered up, then running fsck on reboot won't cause problems, but it its not powered when you reboot without it, better to set the pass level to 0 so fsck doesn't give errors on reboot.  Usually takes me a couple of tries to decide what works best.

--wally.

---

### Post by xenophon on 2006-11-04
Thanks - that was very comprehensive.

So, I guess the best approach would be to enter a value of 0 for the fsck variable, and perform fsck manually.

Which brings me to the next question - performing manual fsck's: what is the optimal procedure to ensure data integrity for my backup RAID array?

Once again, thanks for your time.

Xen

---

