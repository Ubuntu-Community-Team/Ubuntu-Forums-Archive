---
title: "Ubuntu Complitely Won't Start"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by 3DBoom on 2008-02-11
Hi guys

i'm a noobie of the entire Linux world, i've tryed the last 2 versions of Ubuntu on virtual machine and fell in love with this system so i've decided to leave windows xp mediacenter and fully use Ubuntu on my pc...unfortunately Ubuntu won't start

I bought a brand new Maxtor/Seagate 160GB EIDE PATA hdd and placed inside my system, here some specs:

AMD Athlon XP 2400+ (core Thoroughbred)
Mobo GIGABYTE GA-7VA Triton
1GB RAM DDR ( 512 400MHz + 256 266MHz + 256 266MHz)
Video PNY GF FX5600Ultra AGP
AUDIO Hercules CMI8738/C3DX on PCI slot (the integreted one has been disabled in bios)
HDD MAXTOR/SEAGATE 160GB PATA IDE (brand new .. just bought)
DVD-ROM Pioneer (tray in not slot in), DVD+-R/RW NEC 

i've formatted the HDD in NTFS with a primary&unique partition og 160GB (i've done thi by mountig it on a windows based pc) and burnt a cd with the downloaded iso image of UBUNTU dektop x86 7.10 edition

so i'm ready to installa a 100% clean installaiton.

I place my cd into the dvd rom and the initial multiple option screen is shown, i choose the keyboard layout (i'm italian) and language and choose 1...start/install ubuntu.
I can see the cross barr for few sec and than i receive this  black screen:

BUSY BOX V1.1.3 BUILT-IN SHELL etc...
ENTER HELP FOR A LIST OF BUILT IN COMMANDS

(INITRAMFS)_

i can't type any word and the system won't move over.

i've tyed also F4 to set resilution but nothing change, i tried to use the dvd-r/rw instead of the dvd-rom but i always come to that screen. I've also tryed the safe vga and OEM option but nothing chagne.

wondering about a iso/cd problem i've tryed it on my other windows system (athlon 600 mobo msi radeon 9000 quantum hdd lge cd-r/rw 2x256 sdram 133Mhz) and it sucessfully boot the live cd.

I've downloaded the alternate version of ubuntu 7.10 but i got nothing more than a _ blinking on a black screen. Same thing using ubuntu 7.04

Any suggention? As i said this is a "clean new system" with no other os on driver and no other drives attached so i can try everything without concernig about data loss.

Thanks for any comments or help, i'll really appreciate!

Regards
3DBoom

btw: i'm dowloading also 6.90...gonna try also this one and eventually use update  amager to reach 7.10 but it will be easyer to start the 7.10

---

### Post by 3DBoom on 2008-02-12
Hi,

just a small update:

i've tried also UBUNTU 6.90 and the loading hangs. So i removed quiet splash command with F6 and tried to boot...i can see a screen log of operation and this one in repeated for ever:

Unexpected IRQ TRAP AT VECTOR C3

any clue?

i'll have to stay with windows or there is still hope?

Thanks!

---

### Post by Partyboi2 on 2008-02-12
maybe try adding some boot options and see what happens try
acpi=off
[Here]("https://help.ubuntu.com/community/BootOptions") are some more boot options, you might find one that does the trick

---

### Post by 3DBoom on 2008-02-12
> **Partyboi2 said:**
> maybe try adding some boot options and see what happens try
acpi=off
[Here]("https://help.ubuntu.com/community/BootOptions") are some more boot options, you might find one that does the trick

Thanks, i'm gonna try the options

---

### Post by 3DBoom on 2008-02-12
IT WORKED!!!

i used these option, probably more than the truly needed but worked:

at the end after --

(i also removed the quiet splash)

noapic nolapic pci=noacpi acpi=off

finally i'm in ubuntu and i'm currently writing from the new OS in wifi!!!!

Thanks!!!

---

