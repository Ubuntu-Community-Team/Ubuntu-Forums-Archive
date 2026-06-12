---
title: "[SOLVED] Dual Boot problem - Hardy and XP on same disk"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by nickruiz on 2008-05-25
Hey everyone,

I just attempted to perform a dual boot installation of Kubuntu Hardy on a system with XP Pro already running. I followed the instructions at the link below, but for some reason GRUB does not appear at start-up. XP starts immediately.
[https://help.ubuntu.com/community/WindowsDualBoot#head-6852d2e9b3e03d350a4271b58e3bdea4bbe81ad8]("https://help.ubuntu.com/community/WindowsDualBoot#head-6852d2e9b3e03d350a4271b58e3bdea4bbe81ad8")

I got right to the point of restarting my computer after installing Hardy, but it looks like I'm getting the issue mentioned at the link above that may occur with Vista systems:
> Windows Vista may stop your GRUB - Boot manager from reaching (booting ) your Ubuntu installation, when for any reason you try to repair Boot on MBR (Master Boot Record) on your Bootable HDD (Hard Disk Drive).

As a note, I decided to install Hardy on the same hard disk as my XP installation (it's a SATA disk, while my secondary is IDE -- not to mention I already had empty partitions available).

Could someone advise me as to how to get GRUB to run first? As of right now, XP is ruling my PC.

Thanks,
Nick

---

### Post by IHATEDLINK on 2008-05-25
Try to reinstall Kubuntu.

---

### Post by meierfra. on 2008-05-25
Try changing the  boot order in the bios, so that you boot from the IDE drive. Maybe grub got installed onto the IDE drive.


If that does not work, I recommend EasyBCD (see my signature)

---

### Post by nickruiz on 2008-05-25
meirfra, turns out you're right. It installed grub on the IDE drive. Thanks for your help.

---

