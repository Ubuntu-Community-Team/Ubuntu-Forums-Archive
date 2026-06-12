---
title: "Cannot log in (while Ubuntu drums beat continuously in my ears)"
date: 2005-03-15
forum: Installation &amp; Upgrades
---

### Post by mjgeorge on 2005-03-15
I've been having some difficulties installing Ubuntu on my system.  At first, it would lock up while trying to boot Linux.  I then figured out that I needed the "pci=noacpi" option as my motherboard uses VIA chipsets.

Then, the installation seemed to run OK (although there were a few errors that scrolled by a little too fast to read).  When I finally got the the point where the installation was complete, it would hang when I entered my user name and password.  Also the Ubuntu drum sound was playing the entire time (wouldn't quit).

So, a few questions:
1.) Just out of curiosity, what is ACPI?
2.) Are there any other boot options I should use given my system information (listed below)?
3.) Is the information displayed to the screen during installation logged to a file I can read (and if so where is it located)?
4.) Would it be recommended to try installing again (possibly in expert mode), or is there a way to figure out whats wrong with and fix the current installation?

System Info:
CPU: Athlon XP 2000
MB: Asus A7V8X
CHIPSET: Northbridge (VIA KT400), Southbridge (VIA VT8235)
RAM: Kingston 512MB PC2700
HD1: Maxtor 80GB 7200RPM ATA-133 (with Windows XP)
HD2: Maxtor 13GB (can't remember speed, probably ATA-100) for Ubuntu
AUDIO: Realtek 6 channel CODEC
LAN: Broadcom 10/100 Mbps (not attached to anything)
USB: VT8235 built-in USB 2.0
BIOS: Award BIOS, but I'd have do check as to the exact version.
MODEM: Zoom v.90/v.92 voice/data
DVD: Toshiba 16x
CDRW: Liteon 48x/12x/48x
VIDEO: Leadtek Nvidea geForce4 Ti4200 64MB

Thanks,

Matthew George

---

### Post by gungaden on 2005-03-21
Which ISO version did you install?

---

### Post by mjgeorge on 2005-03-21
I believe it was Warty 4.10.

By the way, I was able to log in to the desk top by going into my BIOS and disabling the audio CODEC.

---

