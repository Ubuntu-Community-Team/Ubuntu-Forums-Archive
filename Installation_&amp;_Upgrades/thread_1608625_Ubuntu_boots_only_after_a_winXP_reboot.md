---
title: "Ubuntu boots only after a winXP reboot"
date: 2010-10-29
forum: Installation &amp; Upgrades
---

### Post by trappo on 2010-10-29
I tried to install ubuntu 10.04 on a desktop in dual boot with win XP.

Ubuntu doesn't boot. It only happens after a reboot of win XP.
I upgraded to 10.10 but nothing changed, i made a clean install but still it happens...

I mean:

1. Power on
2. grub -> ubuntu
3. splash screen freezed

otherwise:
1. Power on
2. grub -> WinXP
3. reboot
4. grub -> ubuntu
5. ubuntu run perfectly


How this could happen?!?

---

### Post by oldfred on 2010-10-29
If you do a warm reboot from Ubuntu to Ubuntu does it work?

They have been trying to speed up boot process and BIOS should make sure drive is up to speed before starting boot, but it seems in some cases that some hardware is just not ready and grub/ubuntu is ahead of itself.

Some have added delays to make it work, but I did not save links to those comments.

Do you have a small power supply and have added a lot of devices or new video card that sucks lots of power? Do you have extra devices connected, or do you have things configured in BIOS like floppy but have no floppy and it takes a while to sort that out and causes issues. Check other BIOS settings, update BIOS if not current.

---

