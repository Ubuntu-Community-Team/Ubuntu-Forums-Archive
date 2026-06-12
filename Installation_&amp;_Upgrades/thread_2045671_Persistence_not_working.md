---
title: "Persistence not working?"
date: 2012-08-21
forum: Installation &amp; Upgrades
---

### Post by MrPolarBear on 2012-08-21
I installed Lubuntu 12.04 Desktop to be used as a live USB, however when I made some changes and restarted my computer (Dell E510, all stock except 3gb DDR2) my changes weren't saved. Can someone help with this?

---

### Post by C.S.Cameron on 2012-08-21
Plug your flash drive into a running computer.
Look to see if there is a file named casper-rw on it.
This is the file that stores persistence.
If there is no casper-rw file try making the stick again.
I prefer Startup Disk Creator, (usb-creator), from the Live CD.
UNetbootin also works well.

---

### Post by efflandt on 2012-08-22
What changes did you try to make?

If persistence is working, it will store certain settings like timezone and network or wireless security settings.  And you can add programs that you run after you boot.

However, the system boots a fixed squashfs filesystem before persistent data is mounted, so you cannot add video drivers, update kernels, remove default programs, or stop it from booting as default user "ubuntu" who can do about anything with no password.  So even though you can add users with passwords, anything the other users do that is not encrypted could be accessed by the default "ubuntu" user.

---

