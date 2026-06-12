---
title: "is bootable partition necessary"
date: 2010-03-15
forum: Installation &amp; Upgrades
---

### Post by dnoyeb on 2010-03-15
I know what a partition is, but I have had a heck of a time trying to figure out if a partition MUST be bootable or not.  I know in windows it must be.  And windows expects only 1 bootable partition.  However, when I run fdisk, I can set several partitions to be bootable.

What does this do?  Do I need a bootable partition if I am using a bootloader like GRUB?

Thanks.

---

### Post by ajgreeny on 2010-03-15
You do not need a boot flag for linux, if that is the question you are asking.  For windows, yes you do, or it will refuse to boot.

---

### Post by dnoyeb on 2010-03-15
That is the question.  Thanks for the quick reply.

---

### Post by srs5694 on 2010-03-15
Actually, recent versions of Windows seem to be happy to boot with the active/bootable flag *not* set, at least when GRUB is involved. That flag is necessary for older versions of Windows (those based on DOS/Windows 9x/Me) and when using the DOS/Windows MBR boot loader code rather than GRUB or some other boot loaders.

---

### Post by oldfred on 2010-03-15
Also some BIOS assume windows and will not boot unless there is a boot flag. If you have one of those BIOS you may still need to set a boot flag even though linux does not normally need it or use it.

---

