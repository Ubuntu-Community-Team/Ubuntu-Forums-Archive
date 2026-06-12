---
title: "whats the best way to install ubuntu on my pc?"
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by skakid177 on 2010-06-02
im running xp and id like to run kubuntu on the same machine. should i use that virtual pc software? if possible i want to install it entirely on its own hard drive

---

### Post by lemming465 on 2010-06-04
There is a lot of advice at the [Dual Boot help page]("https://help.ubuntu.com/community/WindowsDualBoot").  In your case, where you want to install onto a second hard drive, you'd need to use *manual* partitioning.  I usually like my dual-boot systems to have GRUB on the disk MBR (master boot record); Ubuntu will do this by default.  It will automatically add windows entries to your boot menu.

---

### Post by lemming465 on 2010-06-04
Um, the previous reply assumed you wanted to switch between kubuntu and windows.  If you want to run both at once, then yes, you need a hypervisor technology.  Assuming your PC has hardware support for virtualization, I'd suggest using virtualbox in your case.  Canonical packages that if you don't want to download it directly from Oracle (which bought Sun).

---

