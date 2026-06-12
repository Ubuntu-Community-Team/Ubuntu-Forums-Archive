---
title: "Problem with installation black screens &amp; hanging"
date: 2015-03-07
forum: Installation &amp; Upgrades
---

### Post by Black Magic on 2015-03-07
I've been trying to install Ubuntu for awhile today and I've ran into a lot of problems.

Most the time when I try to boot from my USB in UEFI it just gives me a black screen after grub. I tried using nomodeset, acpi_osi=Linux, and noacpi, none of these options worked nomodeset did take away the black screen but then it just hung after a few messages about AHCI or initialized DRM. There werent any errors that I saw. The few times I did get into the splash screen, the installer just hung, not very useful since I cant seem to get into it very often maybe 1/10 times.

I've tried legacy but that gave me the exact same problems.

I've also updated the UEFI firmware. I've disabled Fast Startup & Fast boot. 

I dont even know what to try at this point.

---

### Post by Black Magic on 2015-03-07
Fixed. Changed from AHCI to IDE.

---

