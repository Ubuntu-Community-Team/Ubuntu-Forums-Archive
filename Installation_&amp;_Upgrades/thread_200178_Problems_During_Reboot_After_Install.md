---
title: "Problems During Reboot After Install"
date: 2006-06-19
forum: Installation &amp; Upgrades
---

### Post by deboring21 on 2006-06-19
Ok, I installed Xubuntu with the added line "noapic nolapic." I get into the Live interface and install the OS... all goes well there. But when I reboot it, I get past the message "Uncompressing Linux... Ok, booting the kernel." but it hangs after I get another message "[4294669.540000] .. MP-BIOS bug: 8254 timer not connected to IO-APIC" I've tried adding the lines "noacpi" "acpi=off" "pci=noacpi" and many more.. but none have seemed to work. When I don't have "noapic nolapic" before the install starts, I get the MP-BIOS bug thing right away, but when I have those lines in, I don't get that until the reboot after the install... if  you have any suggestions or questions, let me know...
-Ryan
btw.. my pc is an IBM Xserver 220, with 2x 1ghz procs, 3 gigs of memory, 1x36gb and 1x18gb SCSI HDDs, and yeah... My dad has the same machine and his is having the same problems as mine with the whole install... he tried the alternate install CD also, but still no go, so he retreated back to 5.10...

---

