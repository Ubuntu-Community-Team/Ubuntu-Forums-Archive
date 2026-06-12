---
title: "Stops at ACPI: PCI Root Bridge [PCI0] (0000:00)  Newb Help Please!"
date: 2007-02-05
forum: Installation &amp; Upgrades
---

### Post by CodyLoco on 2007-02-05
Hi Everyone!
I'm new to the forums and pretty much new to Ubuntu/Linux and I'm stuck (of course) just like every other newbie.  My problem is with Ubuntu 6.06 for PC.  I know it is not the disk because I reburned the disk about ten times a month ago to no avail, and now I'm using one of the actual pressed versions from Canonical.

Anyways I'm trying to load it onto a Acer Aspire E700 series desktop with a Core 2 Duo E4300, 1GB DDR2, 320GB SATA HDD and the usual built-in Intel graphics chipset.  The livecd stops running after I start the loader, right after it finishes saying "loading linux kernel".  I removed the quiet splash from the boot settings and I found it is hanging in the same place every time.  Here is the screen I copied down gruesomely by hand and then retyped here on another computer (actually running xubuntu).

```
monitor/mwait feature present.
using mwait in idle threads.
CPU: L1 I cache 32k, L1 D cache 32k
CPU: L2 cache: 2048k
mtrr: v2.0 (20020519)
CPU: Intel(R) Core(TM) 2 CPU 4300@1.80GHz stepping 02
Enabling fast FPU save and restore... done
Enabling unmasked SIMD FPU exception support... done
Checking 'hlt' instruction... OK
Checking if image is initramfs... it is
Freeing initrd memory: 6843k freed.
ACPI: Looking for DSDT... Not found!
ENABLING IO-APIC IRQs
.. TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
NET: Registered protocol family 16
EISA bus registered
ACPI: PCI BIOS revision 3.00 entry at 0xfa020, last bus=2
PCI: Using MMCONFIG
ACPI: Subsystem revision 20051216
ACPI: Interpreter enabled.
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (0000:00)
(SYSTEM HANGS HERE)
```

Can someone please help me out?  I should also mention that this is also the second Acer computer I tried to install Ubuntu onto (last one was a Pentium D proc) and it was hanging in the same spot.

As always thanks in advance!
~Cody

---

### Post by CodyLoco on 2007-02-06
I got it to work!  (After about three hours of tinkering...)

Anyways, however, I'm now stuck on the apparently infamous x server error.  It basically tells me the server crashed, but doesn't tell me any error codes or anything.  It looks like an error window tried to pop up but then I just get sent into the command prompt.  I honestly have no idea as to what to do from here on, could someone point me in the right direction?

---

### Post by driedger on 2007-03-20
Hello, I am having the exact same problem with an acer aspire e700 I just picked up. I dont consider myself a newbie, but I must be missing something, as I cannot get it to boot past the same spot ACPI: PCI Root Bridge [PCI0] (0000:00)

As for booting, I actually am having a lot of trouble getting any linux distro to boot on this new machine. Whats the trick to making it work?

thanks,
Mark

---

### Post by driedger on 2007-03-20
anyone?

---

### Post by dghelani on 2008-02-12
Mee too .. having the same problem.... btw what all tinkering i require to do... to get the error message....?

---

### Post by breaking on 2008-02-12
use kernel param acpi=off

---

### Post by erginemr on 2008-02-12
If "acpi=off" works for you, go with that . But if the problem persists after the hard drive installation, then setting "acpi=off" is not the best thing to do, because it means shutting down an entire range of functionalities related to acpi. Could you please try:
```
acpi_irq_balance
```
and also
```
pci=noacpi
```
after the following community manual:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Using "acpi_irq_balance" has also been the remedy of another Ubuntu user somewhere within the forums.

---

