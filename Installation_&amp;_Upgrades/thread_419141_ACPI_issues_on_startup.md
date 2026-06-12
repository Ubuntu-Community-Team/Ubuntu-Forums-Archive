---
title: "ACPI issues on startup"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by doanster on 2007-04-22
first
using a box with a Aopen AK77-333 board and a ati pci video card - ACPI is turned off in the bios

any install i do (regular or alternate) must be done with the added string  pci=noacpi  acpi=off
the install will finish successfully and then on restart get to the " starting up" and then hang

went into text mode and get down to the following line where it will hang (inc a few lines before)

100.993873] early unpacking initramfs...done
101.594367] ACPI Core revision 20060707
101.602031] looking for DSDT in initramfs...file DSDT.aml not found      using machine DSDT
101.605329] ACPI: setting ELCR to 0200 (from 1E00)

this is as far as i get

any help on fixing this appreciated
please be detailed as new to linux

thanks   doanster

---

### Post by richtl on 2007-04-22
I just ran into a similar issue. I've been running Feisty without problems since Friday. After this evening's update, I get the following error while booting (even in failsafe mode):

ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using maching DSDT.

My machine then hangs indefinitely. 

Disabling SATA in bios fixed the problem. Very nasty!

---

### Post by doanster on 2007-04-22
Unfortunatly - No SATA on this board

looking for any other suggestions or workarounds

thanks

doanster

---

### Post by 96west on 2007-04-23
Noobie, oldie, no pro or hobby tech skills..

I can't get to all the data lines you mention etc. HOWEVER, Puppy Linux taught me something this morning, after a couple days of failed Start or Install attempts on Ubuntu CDs I burned.

I burned a Puppy CD and the usual fail happened after the initial screen, but Puppy had a solution staring me in the face. On a list of several alternate startup modes, when I chose the one to tell Puppy acpi=off rather than what it says is default, acpi=on, it produced a swift and successful Start for Puppy running on Ram alone as it wants to do......no problem after that.

So now if I could tell Ubuntu installers to understand the necessity of acpi=off, I might get it installed, it would seem.

Any guidance on how to make changes in BIOS or get to such a choice on Ubuntu installs would really help.

---

### Post by doanster on 2007-04-23
Have gotten to the boot scrip and edited to say ACPI=off

Still only get the point indicated in original email

HELP

---

