---
title: "Trying to install ubuntu on a friends computer no acpi boot error."
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by Vigh on 2008-06-28
Hi it comes up with no acpi, try booting with no-acpi mode. How do I do this exactly and what does this mean.

---

### Post by dominiquec on 2008-06-28
On GRUB, just after you boot up, press 'e' to edit your boot line.  Add acpi=off to the kernel line (the one with vmlinuz).  Then boot.

---

### Post by VMC on 2008-06-29
> **Vigh said:**
> Hi it comes up with no acpi, try booting with no-acpi mode. How do I do this exactly and what does this mean.

Here is a link with some information: [http://ubuntuforums.org/showthread.php?t=201089](http://ubuntuforums.org/showthread.php?t=201089)

Is this for a laptop? I'm not sure if that's advisable. Since ACPI controls fan and power features. I have been fighting this with my desktop. I have a faulty DSDT table. I turned it off one time with my laptop and the tempature went to high.

Here's some heavy reading regarding the issue:
[http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface](http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface)

---

