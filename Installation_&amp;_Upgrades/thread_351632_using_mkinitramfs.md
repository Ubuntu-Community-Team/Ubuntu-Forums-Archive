---
title: "using mkinitramfs"
date: 2007-02-02
forum: Installation &amp; Upgrades
---

### Post by saikumar_divvela on 2007-02-02
Hi,

I have installed ubuntu 6.10 on my system. It uses kernel 2.6.17-10-server
I want to see the contents of boot image initrd.img-2.6.17-10-server.
I think this image is created using **mkinitramfs**.

From internet i found that old kernels are using **mkinitrd **for creating images where as for  kernel above 2.6.12 mkinitramfs should be used for creating images. Please clarify this.

mkinitrd uses **cramfs **file system for creating images and **cramfsck  **can be used to extract the contents of image.

It seems mkinitramfs doesn't use the cramfs file system and cramfsck   is not working.

What is the file system used by mkinitramfs?
What is the tool/command  required for extracting the contents of image created by mkinitramfs. 
Please help me.


Thanks & Regards
Sai

---

### Post by mburgess00 on 2007-02-11
mkinitramfs creates a gzipped cpio archive. Create a temporary directory, say /tmp/initrd. cd to that directory then run:

cat /boot/<initrd you want to extract> | gunzip | cpio -ivdm

and it will be extracted.

-Matt

---

