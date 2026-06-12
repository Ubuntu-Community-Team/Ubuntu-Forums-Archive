---
title: "Ubuntu Installation unexpectedly modifies itself"
date: 2016-04-27
forum: Installation &amp; Upgrades
---

### Post by bcalvertfl on 2016-04-27
So every time I try a fresh install of Ubuntu, I continue to get the same issues as the last... Modified name server, unauthorized dpkg links, OpenSSL, NBios, SSH, VPN, PHP5, you name it... Unable to make any changes to the packages due to policy settings nor can I modify the network manager files since it retrieved a backup of the previous setup via /proc/ location. Is there anyway to get past this and restore it to a legitimate installation? I've tried using a LiveCD, tried removing the HDD and starting from scratch, no matter what I attempt it's always another iteration of the same issue. I was able to get some of the log files if they might help...
[https://drive.google.com/open?id=0BzgsQH8uq2bmTXU3V2xRSnRlNGc](https://drive.google.com/open?id=0BzgsQH8uq2bmTXU3V2xRSnRlNGc)

---

### Post by DuckHook on 2016-04-28
*Your thread has been moved to **Installation & Upgrades** as a forum that is more relevant to your problem.*

I have also changed your title to more closely describe your report.

---

### Post by bcalvertfl on 2016-04-28
> **DuckHook said:**
> *Your thread has been moved to **Installation & Upgrades** as a forum that is more relevant to your problem.*

I have also changed your title to more closely describe your report.

Thanks man, sorry for the misdirection!

---

### Post by bcalvertfl on 2016-05-02
Bump! Still an issue!

      Even with a LiveCD of other distro (Kali). I also dug out an old Windows disk and gave it a try... Windows got destroyed worse than Linux did... Although it did help me figure a few things out... Apparently running netstat shows a NBNS and RCP service that boots alongside the install that cannot be stopped without deleting the source file. Tried changing the default account passwords, local security settings, and various ports through my firewall on my router. Worked for awhile until the event viewer security logs showed the SYSTEM login changing and deleting registry keys until Windows crashed. I never got it past "Please Wait" Windows 8.1 splash screen; hung after that (although booting into WinRE and digging around with the CMD showed a lot of registry keys that were added/removed) and if I open the WINSETUP.dll with notepad, the parts I CAN view all point to various changes to DCOM, APIs, WMI, etc (plus it had a lot of callback commands that refused to let the installation cancel).
      Somewhere along the way my entire USB was formatted so I'll have to create another in Kali later today and dig around more but honestly I'm out of ideas. The only possible thing I can think of is maybe my ROM was modified for SRAM tables since I physically cold booted the system yesterday (i.e. removed HDD, PCI, USB [keyboard and mouse only], disconnected power, reset then removed CMOS, power cycled a few times, reinstall CMOS and plugged power only back in) or modified firmware in the UEFI, optical drive, or maybe even the router itself... Seems like a lot of trouble to go through, lol, I'll try flashing the BIOS today after pulling a copy of it and seeing what flashrom has to say... Any other ideas would be great! &#55357;&#56842;

Here are some logs I managed to pull from C:\ via the CMD in WinRE.
[https://drive.google.com/open?id=0BzgsQH8uq2bmeFRzNFFQNG9yN2s](https://drive.google.com/open?id=0BzgsQH8uq2bmeFRzNFFQNG9yN2s)

---

