---
title: "Unable to install server... hangs on 'checking hlt instruction'"
date: 2006-07-29
forum: Installation &amp; Upgrades
---

### Post by Huskyr on 2006-07-29
Hey everyone,
i've unsuccesfully tried to install 6.06 Server on my old machine so that i can use it as a router and file server. 

Here are the specifications:
CPU: Cyrix MII-266 (200 mhz)
RAM: 72MB (one 64MB SDRAM, one old 8MB SIMM)
HD: 3,2GB IDE
A general PCI display adapter
40x CDROM drive

Whenever i try to install the installer hangs when going to the 'Uncompressing kernel...ok, booting the kernel' message. I've tried switching some things off (as found in the help system) using:

```
install acpi=off noapic nolapic
```

But this doesn't really help.. I've tried the expert installation and found out that the system actually does start booting but hangs on this message:

```
checking 'hlt' instruction....ok
```

I've already tried an older (5.10) Ubuntu installation cd to see if it might be my burned copy of 6.06 but that installation also hangs, at another message though:

```
checking if image is initramfs...it isn't (no cpio magic); looks like an initrd
```

Does anyone have any clues how i might resolve these errors and start the installer?

---

