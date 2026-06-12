---
title: "Grub installation."
date: 2004-10-20
forum: Installation &amp; Upgrades
---

### Post by fps on 2004-10-20
Hi

Does Ubuntu automatically install Grub in the mbr or can it be installed in the /boot partition?

I usually have something like:
```

   /dev/hda1          small Fat16 partition       XOSL
   /dev/hda2          NTFS                                WinXP &#40;if needed&#41;
   /dev/hda5          swap
   /dev/hda6          /boot
   /dev/hda7          /
   /dev/hda8          /usr
   /dev/hda9          /opt
   /dev/hda10        /home
   /dev/hda11        /var
   /dev/hda12        /tmp
   /dev/hda13        /vmware

```
for my partitioning so I would install Grub in /dev/hda6.

Hopefully I can do that in Ubuntu.

Thanks.[/code]

---

### Post by jhigz on 2004-10-20
No, the installer allows you to chose where grub is to be installed.

---

### Post by fps on 2004-10-21
Ok. That's a good thing. Thanks.

---

