---
title: "Can't reach install..."
date: 2005-11-07
forum: Installation &amp; Upgrades
---

### Post by Heretic Monkey on 2005-11-07
I've been trying to load ubuntu onto my eMachines AMD 64 box, but i can't even get to the install menu for some reason.  I have tried both the install disc and the live cd, and both refuse to boot what-so-ever.

Trying to run a regular boot i get:

**ohci_hcd 0000:00:3.1: Unlink after no-IRQ?  Different ACPI or APIC settings may help**

After changing the boot parameters to *live hdc=nodma debian-installer/probe/usb=false noacpi nolapic*....

I get **<0> Kernel panic - not syncing:  Attempted to kill the idle task!**

I'm trying to install (hell, even run the live cd) onto my secondary harddrive, so i won't have to worry about any partitions on my master drive, but i can't even get to the installation process.  

Lil help for a n00b?

---

### Post by Kapre on 2005-11-07
[QUOTE=Heretic Monkey]I've been trying to load ubuntu onto my eMachines AMD 64 box, but i can't even get to the install menu for some reason.  I have tried both the install disc and the live cd, and both refuse to boot what-so-ever.

Trying to run a regular boot i get:

**ohci_hcd 0000:00:3.1: Unlink after no-IRQ?  Different ACPI or APIC settings may help**

After changing the boot parameters to *live hdc=nodma debian-installer/probe/usb=false noacpi nolapic*....

I get **<0> Kernel panic - not syncing:  Attempted to kill the idle task!**

I'm trying to install (hell, even run the live cd) onto my secondary harddrive, so i won't have to worry about any partitions on my master drive, but i can't even get to the installation process.  

Lil help for a n00b?[/QUOTE]


Heretic - Did you d/l the cd? I have the same problem (actually mine froze half way - then reinstalled and got the same error as yours). But it turns out that I have a bad d/l cd...Try checking the disc or if you have time burn another one on a slower speed.

K

---

### Post by Heretic Monkey on 2005-11-07
Nah, i got the cd from Linux directly via their free-cd thing.  I got 2 AMD 64 and 2 Intel disks, and neither of the 64 discs work (and i really don't want to have a AMD 64 box and use a 32-bit OS).....

---

