---
title: "How to install ubuntu over (not side by side) Windows 10?"
date: 2021-07-09
forum: Installation &amp; Upgrades
---

### Post by palmgrower on 2021-07-09
I have an old laptop. I installed Windows 10 temporarily (no product key). I want to fresh install ubuntu and wipe out Windows 10. How can I do that?

I downloaded ubuntu 20 LTS iso, and burned it on DVD, inserted the DVD, installed ubuntu. But ubuntu does not start. Side by side installation of ubuntu seems to be the default mode. How can I avoid this and fresh install (format hard drive)? Thank you.

---

### Post by mikewhatever on 2021-07-10
There should be an option of "Erase and install Ubuntu", likely after the dual boot one. All you need to do is select it, and proceed.
For more info, check the installation guide:
[https://ubuntu.com/tutorials/install-ubuntu-desktop#6-allocate-drive-space](https://ubuntu.com/tutorials/install-ubuntu-desktop#6-allocate-drive-space)

---

### Post by grahammechanical on 2021-07-10
> Side by side installation of ubuntu seems to be the default mode. How  can I avoid this and fresh install (format hard drive)? Thank you.

Not default. We get options. See section 6 of the Ubuntu install guide

[https://ubuntu.com/tutorials/install-ubuntu-desktop#6-allocate-drive-space](https://ubuntu.com/tutorials/install-ubuntu-desktop#6-allocate-drive-space)

> : Options related to side-by-side installation or erasing a previous  installation are only offered when pre-existing installations are  detected.

Selecting to erase disk and install Ubuntu would have removed Windows. Over the years few people wanted to erase an existing install of Windows. They often had some need to use Windows.  So, the option to install side by side was given prominance.

Does this old laptop have a BIOS or UEFI motherboard? I assume that Windows 10 was installed in UEFI mode. If so, then Ubuntu must be installed also in UEFI mode. Otherwise problems like this happen. This guide explains it all.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards

---

