---
title: "Ubuntu 20.04.2.0 amd64 desktop Error message when booting the operating system."
date: 2021-03-21
forum: Installation &amp; Upgrades
---

### Post by 1-ahz-1 on 2021-03-21
Good afternoon.

I decided to install ubuntu 20.04 on my computer, starting by making the USB bootable, deactivating the fast startup of windows, giving a delay time of 5 seconds in the bios configuration and when starting the computer with the ubuntu operating system it shows me the following error message:

[0.416518] ACPI BIOS Error (bug): Could not resolve symbol [\ _SB.PCI0. GPP2. BCM5], AE_NOT_FOUND (20200528 / dswload2-162)

[0.416536] ACPI Error: AE_NOT_FOUND, During name lookup/catalog (20200528 / psobject-220)

[0.746701] pci 0000: 00: 00.2: AMD-Vi: Unable to read / write to IOMMU perf counter.

The title if possible could suggest a more suitable one for this error, please.
and also let me know what information would be necessary to facilitate the solution.

---

### Post by CelticWarrior on 2021-03-21
Welcome.

If this errors don't prevent booting successfully (and with all hardware working as expected) you can ignore them.

---

### Post by ActionParsnip on 2021-03-22
I found this
[https://stackoverflow.com/questions/62827591/amd-vi-unable-to-read-write-to-iommu-coun-problem-loading-x-509-certificate#63112560](https://stackoverflow.com/questions/62827591/amd-vi-unable-to-read-write-to-iommu-coun-problem-loading-x-509-certificate#63112560)
but if it's not causing any issues then I'd just ignore it as advised by CelticWarrior rather than tweaking the system for the sake of what is essentially, a warning

---

### Post by 1-ahz-1 on 2021-04-07
Thank you very much, perform the installation of the operating system ignoring the warning message and during the time that I have been using it I have not had problems for it.

---

