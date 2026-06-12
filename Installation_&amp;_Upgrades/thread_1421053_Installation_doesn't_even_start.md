---
title: "Installation doesn't even start"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by whiskeylover on 2010-03-03
I kept getting the "8254 timer not connected to io-apic" bug when trying to install Ubuntu.

I checked the noapic option in Advanced options. Now when I try to install, or run the Live version, it gives a blank screen with a blinking cursor. 

I've tried Ubuntu 9.10, Ubuntu 9.04, Xubuntu 9.10. Nothing works. Each version ends up at the empty screen with the blinking cursor.

Can anyone tell me where to start debugging? Disconnect HDD and that kind of stuff. Please help.

---

### Post by lidex on 2010-03-03
Have you tried this:
[http://ubuntuforums.org/showthread.php?t=909367]("http://ubuntuforums.org/showthread.php?t=909367")
[http://ubuntuforums.org/showthread.php?t=506160]("http://ubuntuforums.org/showthread.php?t=506160")
[http://ubuntu-ky.ubuntuforums.org/showpost.php?p=7795246&postcount=4]("http://ubuntu-ky.ubuntuforums.org/showpost.php?p=7795246&postcount=4")

You can also try disabling apic/acpi in the bios. How old is your motherboard?

---

### Post by whiskeylover on 2010-03-03
> **lidex said:**
> Have you tried this:
[http://ubuntuforums.org/showthread.php?t=909367](http://ubuntuforums.org/showthread.php?t=909367)
[http://ubuntuforums.org/showthread.php?t=506160](http://ubuntuforums.org/showthread.php?t=506160)
[http://ubuntu-ky.ubuntuforums.org/showpost.php?p=7795246&postcount=4](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=7795246&postcount=4)

You can also try disabling apic/acpi in the bios. How old is your motherboard?

Thanks for responding. I tried all those advanced options (noapic, nolapic, apic=no). But nothing seems to work.

I didn't try the text based installer though. I'll try it this weekend :(

I have no idea how to disable it in bios. And I have no idea how old my motherboard is because I bought this computer used about a year ago to serve as a file/web/ftp server for my LAN.

---

### Post by RJARRRPCGP on 2010-03-03
Usually not required to disable ACPI unless your motherboard is older than 2000. ACPI was immature with some motherboards before 2000. (or before 2001)

And usually not required to disable APIC unless your motherboard is older than 2004.

---

### Post by whiskeylover on 2010-03-04
Its not that old. I bought it, used, about a year ago. Its got 4 gigs of memory, and really doesn't look that old.

I tried the text based installer using Ubuntu's minimal CD. Didn't work. I still got the damn empty screen with a blinking cursor.

Funny thing is that a couple of months ago it was running XP and Ubuntu 9.04 with dual boot. No idea what happened.

Any idea on how to diagnose hardware/BIOS errors?

---

### Post by whiskeylover on 2010-03-04
Okay, I managed to boot the computer on the Live CD by unplugging both the hard disks. Maybe one the hard disks is toast. I'll report my findings.

---

### Post by whiskeylover on 2010-03-04
Okay, so the smaller of the two hard disks is screwed. The computer boots with only the bigger hard disk. When the other hard disk is attached, it fails to boot. Is there a way to check this smaller hard disk for errors?

---

### Post by lidex on 2010-03-04
Have a look here:
[http://ubuntuforums.org/showthread.php?t=208689]("http://ubuntuforums.org/showthread.php?t=208689")
[http://ubuntuforums.org/showthread.php?t=30878]("http://ubuntuforums.org/showthread.php?t=30878")

Are these drives both of the same type? I've seen issues with conflict between pata/sata on certain motherboards.

---

### Post by whiskeylover on 2010-03-04
Thanks for your response, Lidex. But my problem is that the computer refuses to boot when the broken harddisk is connected. I have to physically disconnect it from the motherboard for the computer to boot. :(

---

### Post by lidex on 2010-03-04
> **whiskeylover said:**
> Thanks for your response, Lidex. But my problem is that the computer refuses to boot when the broken harddisk is connected. I have to physically disconnect it from the motherboard for the computer to boot. :(

Gotcha.

---

