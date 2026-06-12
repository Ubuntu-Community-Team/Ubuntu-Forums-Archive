---
title: "Boot Repair creates second Windows menu entry (mbr system)"
date: 2017-11-02
forum: Installation &amp; Upgrades
---

### Post by kansasnoob on 2017-11-02
I've been fiddling around and I notice if I set up a fresh dual-boot of Windows 10 and Ubuntu Xenial initially there is only one boot entry in the grub menu for Windows. But if Windows 10 has a small system partition (which is almost always the case) once I run Boot Repair the menu then displays two menu entries for Windows (one for sda1 and the other for sda2). I'm curious what actually changes? It's largely harmless because selecting either menu entry does boot Windows but i'm just curious what changes????

---

### Post by oldfred on 2017-11-02
So many users did not know that Windows since Windows 7 normally creates a separate boot partition (which you do not normally see in Windows) and they incorrectly delete that partition as not something they need.
But it has the only copies of bootmgr & BCD. So then major issues repairing from Windows repair disks which most users do not make. And Boot-Repair cannot fix most Windows issues.

So Boot-Repair copies bootmgr & BCD to main install partition as a backup. And grub does not use boot flag like Windows, but looks for the standard Windows boot files bootmgr & BCD to know which are bootable partitions and then os-prober finds two partitions with boot files & adds both to grub menu.

---

### Post by kansasnoob on 2017-11-02
Cool, that makes sense. I can see how that would be a life saver for future goof-ups.

---

