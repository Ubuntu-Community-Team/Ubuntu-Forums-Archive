---
title: "help adding fedora to grub2"
date: 2009-10-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by woodbj on 2009-10-22
I need help getting Fedora 12 in grub2 because i can't boot into it.

---

### Post by cecilpierce on 2009-10-22
Here is what I put in /boot/grub/grub.cfg:

menuentry "Fedora 12    on  b3" {
    set root=(hd1,3)
    linux /boot/vmlinuz-2.6.31.1-56.fc12.i686 ro   root=UUID=7bd5bb1c-9ad3-4095-acf9-713816c
32916  LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /boot/initramfs-2.6.31.1-56.fc12.i686.img
}

Third line "linux to "quiet" is all one line and change "set root=(hdx,x) to where its at and then sudo update-grub.

---

### Post by kansasnoob on 2009-10-22
Which OS was installed last?

Better yet, post the output of:

```
sudo fdisk -l
```

And what you know about your partitioning.

---

### Post by cecilpierce on 2009-10-22
I had KDE4 on sdb3 and dumped it to try Fedora 12.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1477    11863971    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            1478        2491     8144955   83  Linux

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f8000b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3067    24635646   83  Linux
/dev/sdb2            3068        3200     1068322+  82  Linux swap / Solaris
/dev/sdb3   *        3201        6133    23559322+  83  Linux
/dev/sdb4            6134       12161    48419910    5  Extended
/dev/sdb5            6134        9604    27880776   83  Linux
/dev/sdb6            9605       12161    20539071   83  Linux

---

### Post by kansasnoob on 2009-10-22
So what happens right now when you reboot?

---

### Post by cecilpierce on 2009-10-22
Grub menu comes up and I select which OS I want to use.

---

### Post by kansasnoob on 2009-10-22
> **cecilpierce said:**
> Grub menu comes up and I select which OS I want to use.

Arrgh. Must think, need coffee!

What I'm trying to find out is which OS "owns" or is "home" to the Grub 2 text files.

This situation is right up "ranch hands" alley! 

[http://ubuntuforums.org/showthread.php?t=1285897&highlight=grub+ranch+hand](http://ubuntuforums.org/showthread.php?t=1285897&highlight=grub+ranch+hand)

On to the coffee!

---

### Post by kansasnoob on 2009-10-22
Coffee's not done yet but MY problem is that I'm trying to ask the OP questions, and someone else  is either being cute or thinks they're being sly!

---

### Post by kansasnoob on 2009-10-22
> **woodbj said:**
> I need help getting Fedora 12 in grub2 because i can't boot into it.

I've learned that the very first thing to try with grub 2 is simply:

```
sudo update-grub
```

I've found that works 90% of the time. The one flaw is that it sometimes adds too much (ie: adding os's /home partitions, etc) but it's steadily improving.

---

### Post by VMC on 2009-10-22
> **woodbj said:**
> I need help getting Fedora 12 in grub2 because i can't boot into it.

Show us your menuentry as cecilpierce has shown.

---

