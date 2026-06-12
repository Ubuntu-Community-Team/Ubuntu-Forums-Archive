---
title: "Bootloader question"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by Christian Lindberg on 2008-02-20
Hello there everyone, I have come to a point where I need to reinstall two of my three OS'es for various reasons, and the question I'd like to get answered is if I reinstall XP and then Ubuntu, will GRUB still find Vistas bootloader after XP have overwritten the MBR?

---

### Post by sandysandy on 2008-02-20
should not be a problem.

---

### Post by Christian Lindberg on 2008-02-20
Excellent!

---

### Post by Christian Lindberg on 2008-02-20
Right, I've reinstalled XP now and Ubuntu, but I have a problem, XP don't show up when GRUB loads, instead Vista Longhorn (Loader), the one for Vista shows up, but when I start it, XP start and thus I cannot access Vista, and I do need all my operating systems, how should I fix this?

---

### Post by Christian Lindberg on 2008-02-20
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3e3c3e3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    30716279    15358108+   7  HPFS/NTFS <- XP 
/dev/sda2        30716280   177518249    73400985    5  Extended
/dev/sda3   *   177518592   234438655    28460032    7  HPFS/NTFS <- Vista
/dev/sda5        30717952   149501951    59392000    7  HPFS/NTFS
/dev/sda6       172955853   177518249     2281198+  82  Linux swap / Solaris
/dev/sda7       149517018   172955789    11719386   83  Linux <- Ubuntu

Partition table entries are not in disk order

It senses boot at sda3 that is supposed to be Vista, but instead XP boots, I've never seen such a problem, anyone know what the .... to do?

---

### Post by maybeway36 on 2008-02-20
If you install XP then vista, Vista puts its bootloader in the XP partition. So you can't reinstall XP without reinstalling Vista afterwards. This is always one of the things I hated about Windows.

---

### Post by Christian Lindberg on 2008-02-20
I actually did that the first time before I started reinstalling everything, and Vista couldn't find XP for some reason, and I thought GRUB would find XP and I went on, but it didn't, I'm starting to think it got something to do with my hard drive setups... 

EDIT: Couldn't I repair the Vista bootloader? I doubt it's harder then the "fix mbr" from XP and then reinstall GRUB... no?

---

