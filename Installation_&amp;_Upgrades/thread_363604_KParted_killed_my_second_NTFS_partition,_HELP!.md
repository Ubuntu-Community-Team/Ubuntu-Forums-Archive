---
title: "KParted killed my second NTFS partition, HELP!"
date: 2007-02-17
forum: Installation &amp; Upgrades
---

### Post by ZenYoga on 2007-02-17
I've installed ubuntu 6.10.
When the installation got to partitioning part I told it to resize my second NTFS partition that is about 40GB. It's a D drive.

Here is the problem, it all went well but now I have a raw D partition without any accesible data, please help! Can I somehow repair it?

---

### Post by canisyursus on 2007-02-17
what did you see the program doing... did it delete and reformat to linux format ????

---

### Post by ZenYoga on 2007-02-17
It resized D partition. Made one linux one swap partition.
Here is the picture from windows in the attachment.

In ubuntu sfdisk -l gives:

hda1 as C NTFS
hda5 as D NTFS

but when I try to mount /dev/hda5 it says that it can't be mounted because errors in partition.
In log it says that it can't be mounted because boot block is damaged or something.
Maybe I just need to write a new boot block or something.

Did anyone had similar problem.

---

