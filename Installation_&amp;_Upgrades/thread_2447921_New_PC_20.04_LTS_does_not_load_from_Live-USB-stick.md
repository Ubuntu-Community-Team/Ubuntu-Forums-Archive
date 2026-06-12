---
title: "New PC: 20.04 LTS does not load from Live-USB-stick - many error messages"
date: 2020-07-29
forum: Installation &amp; Upgrades
---

### Post by amiga4000 on 2020-07-29
Hello everybody, 

after many years I have now assembled a new PC, on which, as usual, a dual boot Windows10 (for playing) and Ubuntu (for working) is to be used.

The system consists of:

* Motherboard: MSI Mag Mortar B550M Wifi
* Graphics card: MSI Geforce GTX 1660 Super
* Processor: AMD Ryzen 5 3600 6-core

Windows10 could (of course) be installed without any major problems, but I'm currently desperate for Ubuntu.

I have already deactivated "Secure Boot" on the motherboard, as well as "fast boot" in Windows. The motherboard itself doesn't seem to have a fast boot option, so I couldn't disable anything there either. I made a Live-USB-stick with the 20.04 LTS, but as soon as I want to boot from it, there are many error messages and nothing works.

Here are the errors with activated onboard LAN:
[ATTACH=CONFIG]286572[/ATTACH]

Here are the errors when I deactivate the onboard LAN:
[ATTACH=CONFIG]286573[/ATTACH]

I have already created a new live USB stick with the Daily_Live_x64 version, but also not a success.Now I've been an enthusiastic Ubuntu user for many years, but as soon as it goes away from just using a working system and goes to the installation / hardware troubleshooting page, I'm helpless like a fish out of the water...[FONT=arial] so that I don't even have a clue what the errors could mean (I searched the internet but didn't really find anything ... but I'm also said to have no Google skills ;) ).[/FONT]

So ... do you have any suggestions on what else I should do here to install Ubuntu on my new computer?

Or is the motherboard just too new and I just have to be patient until there is a new Ubuntu version?

Thank you very much for your effort.

---

### Post by P-I H on 2020-07-29
I don't have this hardware, but I'm planning to build a similar system

The LAN chip on this motherboard is [COLOR=#505050][FONT=&quot]Realtek RTL8125B.[/FONT][/COLOR]
It's not yet supported out of the box.
The wifi chip is Intel® Wi-Fi 6 AX200 and this should be supported.
Try to disconnect the LAN cable and use WIFI when installing with the live USB stick.

---

### Post by amiga4000 on 2020-07-29
Hello,

thx for the reply.
That is what I have already tried (I did remember some similar problems many years ago), but if I turn-off all LAN-regarding setting at the motherboard, the last error-code ("unknown chip xid 641") [FONT=arial]disappears, but that strange "no irq handler"[/FONT]-error codes remain.

---

### Post by amiga4000 on 2020-07-29
Hello,

so after looking arround in the internet, it seems the main  problem (aside the lan-chip) was the graphic card... after adding  "nomodeset" at the GRUB... I could load Ubuntu finally.

---

### Post by ActionParsnip on 2020-07-29
If you use Ubuntu 20.04 rather than the unstable version, is it OK?

---

