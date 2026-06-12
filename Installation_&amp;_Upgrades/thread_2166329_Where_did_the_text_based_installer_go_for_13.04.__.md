---
title: "Where did the text based installer go for 13.04.  I need it for advanced lvm setup"
date: 2013-08-08
forum: Installation &amp; Upgrades
---

### Post by MechaMechanism on 2013-08-08
The GUI installer does not offer advanced LVM setup.  I need the text based installer as it has a more advanced LVM setup.  I am trying to combine 3 disks into one big partition and they are GPT disks.  The boot dir will be on a fourth small disk which will be MSDOS based.  Can someone please tell me how to do what I want to do without using voodoo.  I would also like to avoid using the server installer.  I tried using gparted live cd to make lvm disk, but it can't combine them into one big disk.

I'm so frustrated.

---

### Post by oldfred on 2013-08-09
If booting with a separate drive, you should be able to install to that drive and add LVM drivers lvm2 and then configure your LVM. But supposedly the Desktop installer supports LVM.

They did away with the alternative installer with 12.10 and later releases.
[https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop)
> Users who previously installed using LVM or full-disk encryption via  the alternate CD will find that these installation targets are supported  by the consolidated image in 12.10.

---

