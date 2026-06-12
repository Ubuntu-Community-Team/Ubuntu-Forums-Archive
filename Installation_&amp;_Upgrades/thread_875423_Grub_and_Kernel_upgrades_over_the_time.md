---
title: "Grub and Kernel upgrades over the time"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2008-07-30
My desktop has experienced several upgrades of the kernel. Each time a new entry comes to Grub.

I want to remove older entries completely, not just in Grub, but also all files.

What do I need to do to accomplish that?

bye

R.

---

### Post by iaculallad on 2008-07-30
> **ELMIT said:**
> My desktop has experienced several upgrades of the kernel. Each time a new entry comes to Grub.

I want to remove older entries completely, not just in Grub, but also all files.

What do I need to do to accomplish that?

bye

R.

Navigate to System->Administration->Synaptics Package Manager, click on search button and input "linux-image" as search string (w/o quotation). Find the OLD kernels, right-click on it and select "Mark For Complete Removal". Do the same steps with the other OLD kernels. Once finished marking files for removal, click on Apply. This process will automatically update your GRUB boot file.

NOTE: It's best to leave one OLD kernel, just in case something goes wrong with the newest kernel.

---

