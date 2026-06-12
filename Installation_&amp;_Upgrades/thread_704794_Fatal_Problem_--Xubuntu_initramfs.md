---
title: "Fatal Problem --Xubuntu initramfs"
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by Brendan Hart on 2008-02-22
When I try installing Xubuntu Linux on my laptop it boots initramfs instead of going to the live cd? What is going on?

ok semi bad problem, I looked it up and it some somewhere that I had to tell it where to boot from, and I typed root=/cdrom0
and when it reboot it doesnt load nothing just beeps 4 times and turns off

---

### Post by dstew on 2008-02-22
First, check the CD integrity. There is a menu choice for that. You can also try kernel boot parameters by pressing F6 at the first screen, adding them on the end of the kernel line. Parameters to try are noapic nolapic acpi=off irqpoll. You can try any one alone, or in combination.

The other way to go is to install using the Alternate Install CD. It installs the same Ubuntu system using a text-based installer. You get it from the Download Ubunut page, check the box below the Start Download button.

---

