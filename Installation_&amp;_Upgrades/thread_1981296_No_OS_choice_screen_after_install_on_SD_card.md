---
title: "No OS choice screen after install on SD card"
date: 2012-05-16
forum: Installation &amp; Upgrades
---

### Post by joemilx on 2012-05-16
I have a dual boot laptop with Windows 7 64-bit installed on a OCZ Vertex 4 SSD.  The 12.04 install went notmally until the end when it hung up instead of shutting down.  I forced the shutdown after 10 minutes or so.  ON startup, the PC went right to Windows 7: no choice screen, nothing.

I'd appreciate any suggestions on how to proceed.  I'm fairly proficient with Ubuntu, but this one has me stumped.

---

### Post by darkod on 2012-05-16
Grub probably never installed. You can check this with the boot info script from the link in my signature.

One question, what does "SD card" from the title has to do with anything? It implies you installed onto SD card, not SSD.

---

### Post by drs305 on 2012-05-16
I'd recommend booting a LiveCD and installing Boot-Repair. It should be able to find your installation boot files if they exist and make the repair.

If it can't, it will offer to run the boot repair script which will gather system information which will help us determine what went wrong.

Click the 'Boot Repair' link in my signature line to go to it's page.

---

### Post by joemilx on 2012-05-17
Turns out that the SD card reader on my Acer Aspire One is not available at boot time, hence GRUB cannot find Ubuntu.  When I place the SD card in a small card reader attached to a normal USB port.  all works OK.  On to Plan B.

---

