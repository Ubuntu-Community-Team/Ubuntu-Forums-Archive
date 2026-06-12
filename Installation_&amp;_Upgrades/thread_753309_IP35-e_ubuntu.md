---
title: "IP35-e ubuntu"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by seanbarman on 2008-04-12
Hi, 

A lot of people are having trouble are having installing linux on ip35-e as the sata controllers do not support AHCI. I am using a maxtor sata150 card and could still not get any distro to work with this board. I got Hardy installed in the end with alot of trial and error.

1) I got the cd to boot by adding acpi=off, I could then install hardy but it would crash at login,

2) Add the acpi=off to the kernel line, you can do this on the grub menu by pressing e and adding to line, then press b to boot. Ubuntu booted but usb ports an other issues.

3)I then installed i386 kernel uninstalling all traces of generic kernels ,modules etc.I then rebooted pc.

4) The i386 kernel booted without acpi=off option. everything was working usb etc, but i have quadcore so need smp.

5) I tried reinstalling the generic kernel, rebooted and everything works.
how bizarre!

A bit long winded but it now works.

---

