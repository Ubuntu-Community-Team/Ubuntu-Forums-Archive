---
title: "Boot problem after creating 3rd partition"
date: 2013-05-09
forum: Installation &amp; Upgrades
---

### Post by Jedrek30 on 2013-05-09
Hi everyone,

Hope you are all fine.

Today I got round to creating another partition on my laptop to install Windows Server 2012 as I need to practice for Microsoft exam and something weird happened. I have one disc with one partition with Windows 7, another partition with Ubuntu and another windows data partition and what happened was that after creating 3rd partition the laptop threw and error "error: unknown file system". Wow! For me, it looks like it messed up with Ubuntu bootloader because when you dual boot with Ubutnu next to Windows it installs Ubuntu's bootloader and it looks like it's gone now. I had to restore Windows bootloader and MBR and fixed the problem temporarily, however I am looking for a solution how to restore Ubuntu as I still want it:). Ubuntu was definitely not deleted from disk. Your help will be appreciated.

Take care!

---

### Post by 2F4U on 2013-05-10
It shouldn't be a big issue to recover grub. There are several tutorials available and here are just two of them:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by oldfred on 2013-05-10
Did you try to create partition with Windows? That often converts to dynamic partitions which is a huge issue. Does not work with Linux nor some Windows repair tools.

From 2F4U's first link, post the link to a BootInfo report.

While Vista, it still is the same.
 Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

