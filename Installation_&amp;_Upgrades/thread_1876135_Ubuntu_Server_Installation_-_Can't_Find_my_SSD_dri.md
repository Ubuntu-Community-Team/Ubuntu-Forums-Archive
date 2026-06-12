---
title: "Ubuntu Server Installation - Can't Find my SSD drive"
date: 2011-11-05
forum: Installation &amp; Upgrades
---

### Post by Nokao on 2011-11-05
[COLOR="Red"]I just tryed to install 11.10 server to my server, but the SSD disk _is not found_.[/COLOR]

It's a brand new Sandisk Ultra HDSSD 2,5 60GB.

Can someone help me to find a way to tweak this ?
Maybe some extra options on kernel load before installation ?

Also, wich options is better to put into fstab after installation ?

p.s. I tryed with Windows 7 and the SSDisk works.

---

### Post by papibe on 2011-11-05
How do you have your disk set in the BIOS?  AHCI or IDE?

Regards.

---

### Post by Nokao on 2011-11-05
I don't know because it's in AUTO,
but to what do you suggest me to change this option ?

---

### Post by papibe on 2011-11-06
Yes, that's what I would do.

Regards.

---

### Post by Nokao on 2011-11-06
> **papibe said:**
> Yes, that's what I would do.

Regards.

I don't see AHCI or IDE options ...

I see this:
LBA Supported
Async DMA Multiword DMA-2
UDMA: Ultra DMA-6
SMART: supported

Maybe I have to look after the bios ?

---

### Post by Nokao on 2011-11-11
Can someone help me? It don't works !

OS: Ubuntu Server 11.10
Motherboard: Asus M2NPV-MX
Chipset: NVIDIA GeForce 6150 / NVIDIA nForce 430 MCP
SSD don't works: Sandisk Ultra HDSSD 2,5 60GB

The same OS, already installed on another drive (normal SATA Disk) see the Sandisk Ultra HDSSD 2,5 60GB with no problems.

But during the installation I see (while partition textual editor try to partition the disk) ??? ??? and the installation freezes.

---

### Post by Nokao on 2011-11-12
I resolved using Debian, that works.

---

