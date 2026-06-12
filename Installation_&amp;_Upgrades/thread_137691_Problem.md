---
title: "Problem"
date: 2006-02-28
forum: Installation &amp; Upgrades
---

### Post by nielsrondou on 2006-02-28
hi,

I want to install Ubuntu 5.10 on my laptop (Acer TravelMate 8104).
When I booted my pc with the install-cd, I pressed ENTER for the default installation. Then there was written "Uncompressing Linux... Ok, booting the kernel." But after this sentence, nothing happens anymore!:-k

can somebody tell me what I have to do?
thx

---

### Post by dim_hyder on 2006-02-28
Does the onboard video use shared memory ?

I found that when I installed other distros is that I needed to type "linux mem=120M" (128M of RAM, 8Mb shared for the video card) before the installer would work.

You need to do this when it boots from the CD and you get the boot: prompt.

Hope that helps

Dim_Hyder

---

### Post by nielsrondou on 2006-02-28
I read this topic: [http://www.ubuntuforums.org/showthread.php?t=136095](http://www.ubuntuforums.org/showthread.php?t=136095)
can somebody tell me what happens when I type "pci=noacpi"?
I found out that "This disables the use of ACPI routing information during the PCI configuration stages." but what does this means??
grtz

---

