---
title: "Compaq Notebook: Install hangs @ Sys.check"
date: 2005-03-05
forum: Installation &amp; Upgrades
---

### Post by andyk on 2005-03-05
I'm new to Ubuntu but not new to Linux.  Having issues during the initial system check before install starts.  Hardware:

Compaq 2108US Notebook
AMD Athlon XP-m
40gb HD  hda1: 20gb ntfs (win xp)
               hda2: 5gb ext3
               hda3: 12gb ext3
               hda4: 900mb swap
               1gb: unallocated
512mb RAM

When I pop in the CD and boot I get the standard boot messages, going through system checks then I get to this:

check image: initramf it isn't (no cpio magic) looks to be initrd
freeing initrd memory 2824
NET: Registration Prototype Family 16
EISA: Bus Reg
PCI: BIOS rev.2.10 @ 4xFd87b bus 2
PCI: CONFIG TYPE 1
MTRR: v 2.0
ACPI: Subsystem Rev.20040816

At this point it hangs and I get flashing cursor and the CD drive spins down

I have installed SuSE and Fedora without issue and never had this issue...not sure if it's unique to Ubuntu.  (Installing V.4.10)

andy

---

### Post by alastair on 2005-03-05
Try booting with ACPI off e.g.

linux acpi=off

---

### Post by andyk on 2005-03-06
quick update:  the "linux acpi=off" was the answer.  after that i've never had an easier install.  recognized all hardware, except b'com 94306 wifi (of course!).  no having to manual configure my monitor either.  i'm finally free of windoze !

andy

---

