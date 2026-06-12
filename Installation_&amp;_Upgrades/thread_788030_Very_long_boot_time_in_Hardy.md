---
title: "Very long boot time in Hardy"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by nwcowboysfan on 2008-05-09
After upgrading to Hardy by boot time has gone to 2 to 3 minutes. I receive the following errors when the boot process starts:

Starting up...
[   15.251980]...MP-BIOS bug=8254 timer not connected to IO-APIC
Loading, please wait...

This is where it hangs for for the 2 minutes or so. After this it displays kinit errors for drives that aren't the main Ubuntu partition (I have one drive with a Ubuntu, Windows, and Swap partition). The errors report no image found or something. I had the same timer not connected errors before the upgrade, but it did not effect the boot time. I have already tried turning off apic in menu.lst, did not help. My questions are:

1. Anybody else experience this? If so have you had any luck fixing it?
2. Is there a log file somewhere in /var/log/ that could give me more information?

---

### Post by Pumalite on 2008-05-09
Try:
dmesg

---

### Post by wpshooter on 2008-05-09
Have you tried updating your BIOS to the latest version ?

---

### Post by jbr6700 on 2008-05-10
> **nwcowboysfan said:**
> After upgrading to Hardy by boot time has gone to 2 to 3 minutes. I receive the following errors when the boot process starts:

Starting up...
[   15.251980]...MP-BIOS bug=8254 timer not connected to IO-APIC
Loading, please wait...

Post your specs if possible. I went through a similar situation on a Asus/AMD based system after a BIOS flash to the latest. The issue I found was that the ACPI/APIC tables **DO NOT** conform to the spec as they should for the BIOS. Windows based systems will overlook this due to code compilation from my understanding, but Linux expects things to be correct sometimes. I ultimately had to downgrade the BIOS to a previous version to even get Ubuntu to run on the system.

---

### Post by nwcowboysfan on 2008-05-15
Thanks for the replies. I am not sure what specs you need, but here are some:

Toshiba Satellite L25-S1194
Intel Celeron M 1.4GHz
2GB memory
160G Hard drive
Integrated ATI Graphics

The BIOS is up to date, it was updated while I was running Gutsy and I didn't have any problems. The out put of dmesg was too large to paste, so if there is a section you would like to see I can post that. I looked through it and didn't see anything unusual. If there is anything else I can provide just let me know. It runs great once I log in, but the boot is really annoying.

Thanks again for the help!

---

