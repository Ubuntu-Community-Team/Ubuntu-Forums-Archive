---
title: "Install 6.06 Freezes"
date: 2006-08-16
forum: Installation &amp; Upgrades
---

### Post by Eykonic on 2006-08-16
I can install UBUNTU 5.1 off the CD issued with the book "Beginning Ubuntu Linux" with no difficulty. When I try to install off the CD for UBUNTU 6.06 the installation freezes right at the start. The messgage I can see before the install flash screen pops up is:
"ACPI Unable to locate RSDP"

On the flash screen the following appears:
"Loading essential drives OK"
"Mounting rootfile system "

At this point the installation freezes. How to solve this, please?

---

### Post by mgor on 2006-08-16
take a look at the installation guide[0] and especially 
> /--/ or use the function keys to read the instructions for other boot methods and parameters. If you have problems booting the installer, these instructions document a number of workarounds that may be useful depending on your hardware.

i couldn't find any documentation about the parameters, but i'd guess it's something like typing 'linux acpi=off` or 'linux noacpi` that hopefully will solve your problem.

[0] [https://help.ubuntu.com/community/Installation/I386](https://help.ubuntu.com/community/Installation/I386)

---

