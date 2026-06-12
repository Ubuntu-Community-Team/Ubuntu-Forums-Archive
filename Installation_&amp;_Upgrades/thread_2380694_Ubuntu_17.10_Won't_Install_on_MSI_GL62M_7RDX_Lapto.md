---
title: "Ubuntu 17.10 Won't Install on MSI GL62M 7RDX Laptop"
date: 2017-12-20
forum: Installation &amp; Upgrades
---

### Post by evolutionaryit on 2017-12-20
Hi, 

I've got a new MSI GL62M 7RDX and I'm trying to get Ubuntu 17.10 on it. I have tried to install Ubuntu 17.10 via USB but I doesn't successfully boot. I've tried this with UEFI and Legacy boot options and get nearly identical errors:


Firmware bug within Dmesg output:
[4.440279] tpm_crb MSFT0101:00: [Firmware Bug]: ACPI region does not cover the entire command/response buffer. [mem 0xfed40000-0xfed4087f flags 0x200] vs fed40080 f80
[4.440343] tpm_crb MSFT0101:00: [Firmware Bug]: ACPI region does not cover the entire command/response buffer. [mem 0xfed40000-0xfed4087f flags 0x200] vs fed40080 f80.

Then
Watchdog: BUG soft lockup - Cup#7 stuck for 23s! {plymothd:290}
forever this error continues for many pages...

My questions are:

Anyone seen this or know how to fix it?

Also, how do I copy the boot error log when the system will not even fully boot?


Thanks,
J

---

