---
title: "Problems installing Grub"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by orb360 on 2008-02-01
Ok, so I actually used the search function and couldn't find anything that worked for me so here goes. Note that the installer completes and does not complain about anything. After installation... Vista boots automatically... Obviously the MBR is not being overwritten...

Ubuntu 7.10 (Gutsy Gibbon)

I have 3 harddrives. 2 IDE, and 1 SATA. I also have a SATA DVD drive as well.

Now my boot drive is the SATA drive. It's a 150gb drive with 6 Partitions as follows:

0 - NTFS
1 - NTFS
(the 1024 cylinder thing is fixed right? This is a new BFG mobo...)
2 - ext2 /boot
3 - Extended
4 - ext3 /
5 - linux-swap

The IDE drives are a single partition NTFS each.

Now grub wont install to anything...

root (hd0,2)
root (hd0,0)
root (hd1,0)

all of these return "Error 21: Selected disk does not exist"

Now someone said they switched their drives to "User" in the BIOS, unfortunantly mine only allow "None" or "Auto".

Even if I disconnect the IDE drives, the result is the same.

Any ideas on how to get it working?

---

### Post by orb360 on 2008-02-01
also

root (hd<TAB>

no list...

---

### Post by orb360 on 2008-02-01
Ok... I needed to run grub as root... you may mock me later.

Along the same lines, grub is now in the MBR.. but still giving error 21 when I try to boot from it....

I think it may have to do with the menu.1st so checking it out now

---

### Post by orb360 on 2008-02-01
Ok... its working now. Grub had autoconfigured to root (hd2,2) (why??) but I changed it back to what it should be...

Ubuntu boots... Vista boots... everyone is happy!

---

### Post by logos34 on 2008-02-01
> **orb360 said:**
> Grub had autoconfigured to root (hd2,2) (why??)

Grub is forced to guess the bios boot disk, and it's hard-coded to assume any IDE/PATA drives come before SATA, usually starting with the primary master, hda.  That's where grub bootloader went (hd0).  The sata was seen as third/last (hd2).

---

