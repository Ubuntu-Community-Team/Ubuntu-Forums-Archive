---
title: "ubuntu won't start after installation"
date: 2013-05-03
forum: Installation &amp; Upgrades
---

### Post by jhzheng90 on 2013-05-03
I try install ubuntu in my Acer Aspire 5750g. since ubuntu can't be installed at the first time, so I set the boot option as acpi=off as other people said, which it did work. after I finished installation and restart my computer, I enter grub menu and start the ubuntu, however the computer become black screen. I tried several time but I still couldn't get over this problem. now I delete ubuntu but I got the boot-repair info and hope someone can help me. Thank you very much!

here is link to boot-repair info: [http://paste.ubuntu.com/5631053/](http://paste.ubuntu.com/5631053/)

---

### Post by oldfred on 2013-05-04
You show not Ubuntu install. You only have Windows boot loader and three NTFS Windows partitions. You do have one extended partition that is not very large but does not have any Linux partitions inside it. Was your install to an external drive and you now do not have that plugged in?

If you needed acpi=off to boot live installer, you probably needed that on first and maybe all boots.

---

