---
title: "Post-upgrade 13.10 -&gt; 14.04, system will only boot in recovery mode."
date: 2014-05-02
forum: Installation &amp; Upgrades
---

### Post by zombienerd1 on 2014-05-02
Using the built-in distribution update, I updated the system this morning from 13.10 to 14.04.  I have the splash screen disabled during boot.

When I attempt to boot normally with Grub, nothing fails until it attempts to start the DE - then the screen stays black.  Using CTRL+ALT+F2-F6, nothing happens, I cannot get a terminal screen.  Moments later, the monitor goes into sleep mode.

If I select recovery mode in Grub, and then select continue boot, the DE loads immediately, with no issues.

I am running the open source ATI driver.

What steps can I take to figure out what is happening in the normal boot sequence that is causing the issue?  

Hardware:
AMD Phenom X4 9600
Mobo: Asus M3A78-CM
Ram: 8GB
HDD: Samsung 840EVO 120gb SSD
Video: Sapphire AMD 7770HD ghz edition


I have a strange feeling this is a video configuration issue... But I'm open to all investigative options.

---

### Post by zombienerd1 on 2014-05-02
Added nomodeset back to grub, somehow it had been removed during the upgrade?

System boots normally now.

Hope this helps someone else.

---

