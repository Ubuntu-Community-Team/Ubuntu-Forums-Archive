---
title: "Xubuntu Ubuntu Inspiron 7500 install issues"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by ShogoXT on 2008-03-01
Been trying to get an old Inspiron 7500 working well again for someone. I tried both 7.10 Ubuntu and Xubuntu, but I get the same messages when I try to load up live CD. The laptop has 256MB of ram and a Pentium 3. I also use Alcohol 120% to burn the images.

* Configuring network interfaces....      [Ok]
cat: /var/lib/acpi-support/system-manufacturer: No such file or directory
cat: /var/lib/acpi-support/system-product-name: No such file or directory
cat: /var/lib/acpi-support/system-version: No such file or directory
cat: /var/lib/acpi-support/bios-version: No such file or directory
* Saving VESA state...

Any help would be appreciated. Thank you in advance.

---

### Post by dstew on 2008-03-01
First do a CD integrity test (on the Live CD opening menu). If that checks out OK, you can try kernel parameters to see if you can get the Live CD working. These are entered on the kernel line by pressing F6 at the opening Live CD menu. Often-tried parameters are acpi=off noapic nolapic irqpoll.

If you still can't get the Live CD to boot after trying kernel parameters, use the Alternate Install CD to install Ubuntu. It installs the same Ubuntu desktop as the Live CD, but uses a text-based installer that is easier on your system. Get it from the Download Ubuntu page, just check the box below the Start Download button.

---

