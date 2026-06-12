---
title: "DVD Install- i686 kernel"
date: 2005-10-17
forum: Installation &amp; Upgrades
---

### Post by dcarpenter on 2005-10-17
I just have a question about the kernel that was installed during the DVD install of breezy.  I noticed that when i install breezy from the cd image, the 386 kernel is installed on my p4 3.2ghz machine but when I installed via the install/live dvd, the 686 was installed.  Why is this?

---

### Post by pablo13 on 2005-10-17
Hi ... 

You can install the package linux-686 (o linux-686-smp if your PIV supports hyperthreading) and that will install the kernel you need ... After rebooting using that kernel you can uninstall the linux-386 package and the old kernel pakages (linux-image-xxxx-386)

Hope it helps! Bye,
Pablo

---

