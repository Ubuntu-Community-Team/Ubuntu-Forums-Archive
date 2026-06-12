---
title: "Community doc Installation/FromLinux does not work anymore?"
date: 2007-08-12
forum: Installation &amp; Upgrades
---

### Post by Enselic on 2007-08-12
Hello

As I am not having a working CD writer at hand, I gave a go at the HOWTO on installing Ubuntu from an existing Linux installation, by copying contents of a CD to a small partition, and editing GRUB to bot that "CD-partition"

I followed the guide here: [https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

I am able to boot from the "CD-partition", but after I pick language and keyboard layout, it says it fails to mount the CD. Chaning VT and looking at installer output reveals that it expects a cd to be in /dev/hda or /dev/hdb (I have two 52X CD readers there :)). It obviously can't mount any CD though since I have the CD on /dev/sda8.

I have tried to boot both the Ubuntu 7.04 i386 Server, and also Alternate, with the same result; it can't mount CD.

Does anyone know how I can get this to work?

Thanks!

---

