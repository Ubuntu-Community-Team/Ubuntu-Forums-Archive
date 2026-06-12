---
title: "Ubuntu-installation fails; stalls when setting up cupsys"
date: 2005-07-08
forum: Installation &amp; Upgrades
---

### Post by sindrel on 2005-07-08
I've tried installing both Ubuntu and Kubuntu 5.04 from different CDs, and each time, after booting Ubuntu for the first time for downloading and setting up packages, it hangs when it's setting up cupsys (1.1.23-1ubuntu12).

I've had it running Ubuntu once, as it managed to install itself. But it failed a little, and I was forced to attempt to reinstall. But then it failed. And it's been failing ever since.

My machine is a laptop, booted with "noapic nolapic". A MSI S260. 

Does anybody know how to get around/solve this issue? It's incredibly annoying.

Thanks in advance,
Sindrel.

---

### Post by kufu on 2005-07-12
I have an S260 as well and I've had various install problems too. Installing with

 linux noapic nolapic vga=771 acpi=off

seems to work though but there's a problem with the WiFi switch, I haven't found a way to turn it on yet. Let me know if you find a workaround.

---

