---
title: "Can this be run off an external HD?"
date: 2005-10-01
forum: Installation &amp; Upgrades
---

### Post by GOD on 2005-10-01
As title asks?

---

### Post by jdong on 2005-10-01
1) Please post in correct forum.


2) Installing on USB devices haas mixed reports. It's harmless to try (The setup program will be able to recognize it at install ). The potential failure point is the first reboot, when sometimes the system tries to boot before USB is fully initialized (and as a result panics due to failure to locate boot device).

There are ways to tweak this behavior to work around this. Report back to us if just a plain install works -- if not, we'll help you out if possible.

---

### Post by oldboy on 2005-10-02
I've tried installing on an external USB hard disk attached to a Thinkpad X40, which allows USB booting. Install goes fine except for, unfortunately, the bootloader. I don't want to install the bootloader on my Win XP internal hard drive - I want to put it on the external drive. Unfortunately GRUB fails, regardless of which parameter I use (the hd one or the sda one). It just tells me that it's failed to install.
So I tried to install LILO instead. The external drive has an NTFS partition as well as the partitions for Ubuntu and the swap partition. The LILO install seemed to go OK, but when I rebooted, LILO started fine but then came to a halt - sorry, but I can't recall the error message. In theory (although I'm a real Linux amateur), I think there's no reason why LILO or GRUB can't be used on the external drive provided the BIOS allows the drive to boot, but under the current installation procedure, neither works for me.
My theory is that when I do the install, the internal hard drive is "known" to the system, and the drive enumeration uses that fact. However, when I do the boot from USB, the internal drive is NOT "known" (must be a correct technical term which I'm failing to use here :???: ) so the enumeration gives the USB drive a different "ID" and the boot process fails to find it.

---

### Post by GOD on 2005-10-02
Seems like it just keeps erroring out for reasons beyond my knowledge,So I created a new partiton and installed Ubuntu on the main Hard drive,and have been kicking around on it and experimenting with this OS.Sorry to the Admin for posting here,but as I am new to the forum it gets quit mind boggling were to actually post,until you become a regular member its hard to follow the forum at first.

The PC's bios does allow for USB device Boot,but I didnt have nothing but problems,so i rather set up a dual boot system:rolleyes: and it is working flawlessly here.

---

