---
title: "install without cd"
date: 2007-03-31
forum: Installation &amp; Upgrades
---

### Post by rjfioravanti on 2007-03-31
I am trying to switch my dad to Linux, he has an old laptop but it has no cd drive. It does have a floppy drive and USB port, and a wireless card. 

Is there a way I can install from the internet somehow? I have read tutorials on how to install from an ftp / dhcp server on the same network, but I want to know if there is an easier solution first.

---

### Post by Jussi Kukkonen on 2007-03-31
net boot install is not that difficult, but you are going to need a wired network connection (I think) and support for netbooting (sometimes called PXE boot) in your BIOS. There are a couple of howtos in the wiki.

By the way, it's tftp. A regular ftp server is not going to cut it.

---

