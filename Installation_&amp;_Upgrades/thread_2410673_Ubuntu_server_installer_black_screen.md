---
title: "Ubuntu server installer black screen"
date: 2019-01-18
forum: Installation &amp; Upgrades
---

### Post by spookybathtub on 2019-01-18
Hello.  I'm trying to installer Ubuntu Server 18.04 form a USB stick, and after the first screen that says "Install Ubuntu Server", I just get a black screen with no cursor.  Keyboard caps lock and num lock LEDs do not work.  Same result with server live ISO and with server alternate ISO.  The desktop ISO works fine.  I've tried adding various kernel boot options like nomodeset quiet splash acpi=off nolapic but nothing has worked so far.  There's no error message of any kind, does anyone know how to troubleshoot this?

---

### Post by spookybathtub on 2019-01-18
Working boot parameters from Ubuntu Desktop:
[FONT=courier new]set gfxpayload=keep
linux /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash ---
initrd /casper/initrd.lz
[/FONT]

Non-working boot parameters from Ubuntu Server Alternate:
[FONT=courier new]set gfxpayload=keep
linux /install/vmlinuz file=/cdrom/preseed/ubuntu-server.seed quiet ---
initrd /install/initrd.gz[/FONT]

---

