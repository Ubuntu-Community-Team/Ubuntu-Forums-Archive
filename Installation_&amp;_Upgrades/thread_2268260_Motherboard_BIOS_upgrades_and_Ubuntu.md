---
title: "Motherboard BIOS upgrades and Ubuntu"
date: 2015-03-07
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2015-03-07
One of my PCs is dual-boot Ubuntu 14.02 64-bit /Windows 7 Pro 64-bit.  Performance on Ubuntus side has always been excellent.  Win 7 performance was a major problem until I did a BIOS upgrade.  BIOS upgrade has not noticeable changed Ubuntu performance.  Motherboard is MSI CSM-B85M-P32 and processor is Intel i7-4770K.  Question: how does one know when BIOS and/or chipset upgrades are relevan to Ubuntu?

John

---

### Post by ubfan1 on 2015-03-07
Read the release notes for the specific BIOS upgrade (and all the previous ones which are later than the one you are using).  The general ones like fan-control probably are relevant, maybe a rare specific one applicable to a Windows driver if you are using that proprietary driver, and almost never one just related to Linux (Ubuntu) (but I can think of one relating to the new UEFI key control in which a key needed to boot Ubuntu was put into a wrong database).

---

### Post by Mark Phelps on 2015-03-07
Chipset drivers are installed when Ubuntu is first setup and the hardware is scanned to determine the drivers needed.  Unlike with Windows, you don't follow an Ubuntu install by installing chipset drivers -- as they are already in place.

---

### Post by tgalati4 on 2015-03-08
Generally you don't care about BIOS until something doesn't work.  If you try to install a bigger hard disk and your BIOS doesn't recognize it, then look for a BIOS upgrade.  If your fan spins at high speed all the time, look for a new BIOS.  If you get strange errors during boot or in *dmesg*, that are not related to software (based on an extensive web search), then look for a BIOS upgrade.

If you have an old server, they can often benefit from BIOS upgrades to get Linux to run efficiently.  Some IBM PPC7 servers need a firmware upgrade to be able to run Debian-based distros.  Often a websearch on your hardware and Linux will turn up BIOS fixes needed to run Linux properly.

If you don't have any performance issues, then there is nothing to worry about.

---

