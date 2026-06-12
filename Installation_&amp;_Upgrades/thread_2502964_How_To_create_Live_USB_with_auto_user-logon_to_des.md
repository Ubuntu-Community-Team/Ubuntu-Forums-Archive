---
title: "How To create: Live USB with auto user-logon to desktop, auto connection to WLAN?"
date: 2024-12-08
forum: Installation &amp; Upgrades
---

### Post by huramentzefix on 2024-12-08
How To create: Live USB with auto user-logon to desktop, auto connection to WLAN and enabled remote desktop?

I have an old laptop where the display is shot.
It still has an eMMC installed which might contain valuable data?
I want to install home assistant onto it and manage it via GUI.

But first I need to get all data of the eMMC before wiping it.

My idea is to boot from a linux live distro. I somehow need to blindly guess the bios setting to start from usb, but I have another HP laptop here which mich have the same bios settings?
What I need is a linux distro which automatically logs in the user and goes to the desktop environment with a connection to my wlan and a remote desktop connection enabled.

The question is about auto-login, auto-wlan connection and remoted desktop auto enabling. I am OK creating the live-USB

Can you please guide me in the right direction?

---

### Post by yancek on 2024-12-08
A 'live' system by definition is read only.  If you want a 'live' system with autologin and your wifi connection, you will need to loop mount the iso, copy it to a different directory, take it apart using unsquash software on the filesystem.squashfs file, making the changes and recreating the filesystem.squashfs and then recreating the iso.  Not for the fain of heart or a beginner.

You could do a full install of Ubuntu to a flash drive (probably need 16GB or larger) and use that as you would then be able to set up autologin and wireless.  Expect using an install to a usb to be slow.

---

