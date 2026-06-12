---
title: "Kernel panic with new raw NVMe SSD plugged in 16.04"
date: 2017-08-01
forum: Installation &amp; Upgrades
---

### Post by gshockneo on 2017-08-01
Hello,

I'm running Ubuntu 16.04 on my regular hard disk. Now, I have a new NAND NVMe SSD (Samsung 3.2TB) that I would like to migrate to. So I plugin my new SSD using PCIE NVMe adapter into PCIE slot in order to format and install new Ubuntu on it. But as soon as I plugin new SSD, and when I start my Ubuntu again from my normal hard drive, it does not start. I see some stack trace. My kernel version is 4.4.0-87-generic if that matters.

Let me know if I can provide more details.

Thanks,

---

### Post by BenginM on 2017-08-02
Hiya , welcome to the forums .. i see you're already asked [in ]("https://askubuntu.com/questions/942104/kernel-panic-with-new-raw-nvme-ssd-plugged-in-16-04")

---

### Post by wildmanne39 on 2017-08-02
That is okay he can ask in both places.

---

### Post by Bashing-om on 2017-08-02
gshockneo; Hello;

SSDs require that AHCI ( and if available IOMMU ) be enabled in bios . Sometimes these settings can be difficult to find and set.
Case in point is my old Phoenix bios where It is enabling raid that also enables AHCI .
AHCI == Advanced Host Controller Interface


[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

