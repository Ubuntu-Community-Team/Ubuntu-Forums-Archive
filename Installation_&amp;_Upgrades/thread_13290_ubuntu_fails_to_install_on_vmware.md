---
title: "ubuntu fails to install on vmware"
date: 2005-01-30
forum: Installation &amp; Upgrades
---

### Post by rel on 2005-01-30
Hello,

I'am a gentoo user and wanted to take a look at ubuntu, considering to make
a switch. I've downloaded the live hoary installation iso and burned this on cd.

Made a new virtual machine in VMWare and booted the cd. But, the installation
freezes my laptop as soon as it gets where the install program says:
"Configuring  graphics hardware (the screen may blank)". 
This dialog actually reaches 75%. But then a nasty hard lockup.

I've tried various things, like:

- Changing graphics driver of the host OS, to nv (instead nvidia).
- Booting another kernel (instead of ck one)
- Booting ubuntu with parameters: "linux acpi=off nolapic noapic"
- The parameter to disable frambuffer didn't seem to work, as it
  tried enabling FB afterwards.

Debugging VMWare  doesn't show any usefull information.
I have installed redhat and Windows XP as guests and which work perfectly.

Hope somone can clue or tip me :)


greets, rel.

---

