---
title: "Xubuntu Feisty weirdness"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by Whateverist on 2007-04-20
Adding another buggy upgrade to the heap -

I've done the upgrade to 7.04 on an nx9010 (P4, 600-ish MB RAM, Radeon integrated graphics, wireless through an abused Nintendo USB adaptor with Ndiswrapper). The upgrade itself went fine, but there are two severe problems:

* At random points the computer shuts down complaining about "critical temperature". This is nonsense, there's no way a cool-to-the-touch laptop is 128°C on the inside and Windows is happy, too. Starting with ACPI=OFF (as suggested in another thread) seems to avoid the problem, but for some bizarre reason this makes my USB mouse extremely choppy (the laptop touchpad and all apps keep working smoothly).

* After ~30 minutes of use, the internet connection dies. In the past, physically unplugging and reinserting the wireless adaptor fixed this. Now, both keyboards (one on the laptop, one PS/2) die, Applications->Quit stops doing anything and eventually everything freezes except the mouse pointer.

Neither of these issues existed before.

I realise that this might not be fixeable, but maybe it'll be of use to someone.

---

### Post by turten on 2007-04-22
Please **update your BIOS**. You can download it from HP, you will need a floppy disk.

I've resolved my false temperature readings shutdowns just upgrading my BIOS. Now I'm testing Feisty and no problems in 8 hours. Before the BIOS upgrade I could just run Ubuntu Feisty for minutes.

---

