---
title: "Kubuntu 8.04.1 sticks at BusyBox"
date: 2008-08-09
forum: Installation &amp; Upgrades
---

### Post by Nightfighter89 on 2008-08-09
Hey, I decided to install a distro of Linux (only ever used windows OSs before dating back to '95).  My machine:

[LIST]
[*]AMD Athlon 64 3200+ Venice 2.0GHz Socket 939 Single-Core Processor Model ADA3200BPBOX
[*]DFI LanParty UT RDX200 CF-DR 939
[*]BenQ 16X DVD±R DVD Burner Model DW1655
[*]2 gigs DDR
[*]DIAMOND Stealth S9250PCI256SB Radeon 9250 256MB 128-bit DDR PCI Video Card[/LIST]

When I startup to the disc (burned using [this]("http://www.ubuntu.com/getubuntu/downloading?release=kubuntu-newest&arch=amd64&mirror=http%3A%2F%2Fastromirror.uchicago.edu%2Fubuntu-releases%2F&debug=&download-button=&flavor=kubuntu") image) I get the initial menu with the Kubuntu logo and the option to just try it, install it, test the memory, etc.  The only option that works for me is the memtest and that all comes out fine.  Any of the other options first take me to a screen saying 


> [    52.433679] ..MP-BIOS Bug: timer not connected to IO-APIC



Kernel Alive

and then after a loading screen



> BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)


I have a SATA HDD installed with XP on it but I mean to install kubuntu on an IDE one that's also installed.

Anyone have any ideas?  Help much appreciated.  Thanks.

---

### Post by PmDematagoda on 2008-08-09
At the Kubuntu Live CD menu, press F6 and then add this to the end of the line:-
```
noapic
```
then try booting Kubuntu again.

---

### Post by Nightfighter89 on 2008-08-10
> **PmDematagoda said:**
> At the Kubuntu Live CD menu, press F6 and then add this to the end of the line:-
```
noapic
```
then try booting Kubuntu again.

That seemed to get rid of the bit about the timer not connected, though it still brings me to the BusyBox screen.

---

### Post by Nightfighter89 on 2008-08-13
*shameless bump*

---

