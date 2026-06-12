---
title: "Ubuntu 9.04 64-bit install from USB stick- black screen"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by Pastortom on 2010-03-22
Hi..

Dont have a DVD-burner atm, so trying to install Ubuntu 9.04 64-bit from USB stick (got kingston 4gigs and a couple of SDHC to USB adapters 8gigs)..

Ive tried Unetbootin, Universal USB Installer and LinuxLive USB Creator, to install the Ubuntu 9.04 64-bit ISO to my USB stick..

All 3 boot,

but all 3 of them give BLACK SCREEN.. 

I've tried ACPI=OFF, VGA=774, noapic, nolapic.. butnothing works..

Alyways freezes, and gives black screen..

My computer is a Asus P7P55Deluxe with i5 Intel CPU, 2x 8500GTX nvidia cards, and 2x 2gig Corsair Dominator rams.. + about 12 harddrives connected.. inside a wonderfull Antec 1200 chassis :)

Anyways.. anyone know what im doing wrong?

---

### Post by Pastortom on 2010-03-22
Is this in the wrong section or something?

Its awfully quiet around here nowadays :3

---

### Post by Pastortom on 2010-03-22
Found the issue..

First, let me say, that Ive spent 8 hours back and forth pondering over this.. And Im really really upset :/

Anyways.. I tried USB harddrives and USB sticks with Ubuntu 9.10/10.04 ISO images copied to and made bootable..

I tried DVD's and CD's..

I tried everything.. Black screen, black screen, black screen..

Neither of these worked:
ACPI=OFF
noapic
nolapic
VGA=774
nomodeset

[B]All the time it was ONE simple and yet SIncereLY annoying thing..

Dealextreme COMPOSITE-to-USB video signal converter-gadget..

a USB gadget..

That probably caused Ubuntu to go crazy and freeze.. EVERY single time..[/B]

=(

Oh well..

Atleast I found the issue :D

Now over to why my 8111 Realtek Network card cant for the love of donkeyballs be RECKOGNIZED!! :cry::cry::cry::cry::cry:

---

