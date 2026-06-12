---
title: "Machine won't boot following clean install of 20.04"
date: 2020-04-26
forum: Installation &amp; Upgrades
---

### Post by asb3 on 2020-04-26
I performed a clean install of ubuntu 20.04.  The install was successful, and I immediately tried to reboot.
The machine won't boot.  After displaying 2 flash screens, it hangs with a black screen except for a cursor in the upper left corner. The cursor is not sensitive to mouse or keyboard.

If I go into BIOS and select as boot device the drive with the new installation, I immediately get the black screen with the cursor.

Before the install, I cloned the drive containing the boot partition to a usb stick.  I can boot from the USB stick, and everything is as it was before.  If I examine the drive with the new /boot partition, everything is looks OK.

What should I do?

---

### Post by dino99 on 2020-04-26
Might be relative to the gpu driver: which one should be used ? If its a nvidia for example, you need the kernel headers & build-essential installed first.
If you can read 'journalctl -b' then you might find some issues about the video

---

### Post by asb3 on 2020-04-26
The computer does boot using the ubuntu 20.04 liveCD.

---

### Post by CelticWarrior on 2020-04-26
Disable Secure Boot in UEFI then try to boot normally.

---

### Post by dragonfly41 on 2020-04-26
Boot flags set in target?

---

### Post by asb3 on 2020-04-26
Original installation had lvm turned off.  I reinstalled with lvm turned on, and it worked.

---

### Post by TheFu on 2020-04-26
Please read the Release Notes for 20.04.  Many common problems with workarounds are there: 
[https://wiki.ubuntu.com/FocalFossa/ReleaseNotes](https://wiki.ubuntu.com/FocalFossa/ReleaseNotes)

New releases always seem to have some rough spots that take a few months to nail down.

---

