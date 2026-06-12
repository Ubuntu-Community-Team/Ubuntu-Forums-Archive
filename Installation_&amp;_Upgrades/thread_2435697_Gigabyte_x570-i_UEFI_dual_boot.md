---
title: "Gigabyte x570-i UEFI dual boot"
date: 2020-01-24
forum: Installation &amp; Upgrades
---

### Post by tom.j.tang on 2020-01-24
Hi - Trying to dual boot Win10 and Ubuntu 18.04.3.   When Ubuntu and Windows are installed on different drives.  When I reboot the BIOS splash screen shows up and then I get a mount message '/dev/sda2:.....clean'.  But then it freezes.  I'm really at a loss.

I got this message after I put in verbose mode.  

Any thoughts?

[Build]
Ryzen 3700x
Gigabyte Aorus x570 ITX
32GB 3000 Mhz Corsair 
Radeon 5700 8GB
256 GB SATA  (Ubuntu)
1TB m.2   (Windows)

[BIOS]
Defaults 
+XMP profile 1
+ UEFI boot only
+ Secure boot set to standard but disabled (got rid of the UEFI db can't load message)

---

### Post by CatKiller on 2020-01-24
> **tom.j.tang said:**
> Radeon 5700 8GB

My understanding is that you need a very new software stack for that to work. 19.10 or a pre-release build of 20.04 might serve you better.

---

### Post by CelticWarrior on 2020-01-24
> **CatKiller said:**
> My understanding is that you need a very new software stack for that to work. 19.10 or a pre-release build of 20.04 might serve you better.

+1

The message ending in "clean" is not even an error or warning message, just a statement of fact. What is worrisome is the boot process stopping there which means the GUI isn't loading and yes, certainly related with the problem commented above.

---

### Post by oldfred on 2020-01-24
Last summer AMD released a major update to UEFI to have it work with 19.10.
AMD UEFI/BIOS update for Ryzen 3000 series
[https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good](https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good)

But vendors had to include that in their update of UEFI.
Check that you have latest UEFI from Gigabyte, even new system may have been made a while back & update(s) released later.

Also if SSD, check that you have latest firmware.

---

### Post by tom.j.tang on 2020-01-25
Thanks all for the suggestions.  I have tried 19.10 but it gives me the same results.  When I go to 20.0x I am able to get the install to boot.  However now I'm fighting against the Intel AX200 wifi.  Gives an -110 but will start a separate thread for that.

Thanks!

---

