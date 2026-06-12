---
title: "Kubuntu 5.10-amd64 in HP laptop hangs during install."
date: 2005-11-10
forum: Installation &amp; Upgrades
---

### Post by Salane on 2005-11-10
Can someone help me out here? I amtrying to install Kubuntu 5.10-AMD64 on a HP ZV6100 laptop. During the stage of copying the packages to disk the install hangs. I have tried issuing hdparm -d1 /dev/hdc which only lets the install progress further before the hangup. Could this be an framebuffer error problem? If so, could booting with vga=771 help? I assume this is the vga code for 1280X800.

I have checked the install disk and it is good.
I have Kubuntu 5.1-i386 working on another partition with no problems.

Edit Neither vga=771 nor noapic nolapic worked

---

### Post by Salane on 2005-11-11
As an update, the ubuntu 5.10-amd64 doesn't install as well.

as a further update i got it to install using

 linux pci="noirq"

---

### Post by JorgeLedezma on 2006-02-01
I will try the ubuntu 5.10 in my hp zv6100. Do you install it finally?

I am very new to Linux so I appreciate your help.


[QUOTE=Salane]Can someone help me out here? I amtrying to install Kubuntu 5.10-AMD64 on a HP ZV6100 laptop. During the stage of copying the packages to disk the install hangs. I have tried issuing hdparm -d1 /dev/hdc which only lets the install progress further before the hangup. Could this be an framebuffer error problem? If so, could booting with vga=771 help? I assume this is the vga code for 1280X800.

I have checked the install disk and it is good.
I have Kubuntu 5.1-i386 working on another partition with no problems.

Edit Neither vga=771 nor noapic nolapic worked[/QUOTE]

---

