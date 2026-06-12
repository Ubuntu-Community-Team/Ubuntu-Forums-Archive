---
title: "New PC: Kernel Panic"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by compuboy1010 on 2007-06-19
Hi,

I just put my new PC together:

intel e6600
Asus P5b deluxe
2GB ram mdt
gainward bliss 7600gt graphic card

I put the ubuntu 7.04 CD in that I always use and it says Kernel Panic at the end of the messages and won't do anything anymore.

Please help.

---

### Post by Turboaaa2001 on 2007-06-20
I just posted a question similar to this. I have a E6400 (overclocked to 2.71 w/ stock cooler, just to show off)

Anyway, I posted in a thread called "Kernal is panicking, and pills won't help" and recieved an answer saying to disable the second core.

I am trying to install 6.06 and not Fiesta because I do not have a working burner and I have not recieved the new disk in the mail.  I haven't tried it because I want to know if I can enable the second core after I install. If not then it will not help me since I need both cores running all the time.

I'm in need of the same answer so will someone please help us?

---

### Post by Turboaaa2001 on 2007-06-20
Check this out!!! I tried running the 64bit install and got the same results. What was cool was when I ran 5.10 instead of 6.01 . I got the same error but a more precise message...

I cut it down to just the imprtant stuff:


.073000] CPU: L1 I cache: 32K, L1 D cache: 32K
.073000] CPU: L2 cache 2048K
.073000] CPU: Intel(R) Core(TM)2 CPU      6400 @ 2.13
.073000] Enabling fast FPU save and restore... done.
.073000] Enabling unmasked SIMD FPU exception support... done.
.077000] Checking for popad bug... OK.
.077000] checking if image is initramfs... it isn't (no cpio magic); looks like an initrd
.222000] Freeing initrd memory: 3963k freed
.228000] ACPI: Looking dor DSDT in initrd... not found!
.248000]  not found!
.261000] ENABLING IO-APIC IRQs
.262000] ..TIMER: vector=0x31 pin1=0 pin2=-1
.263000] ..MP-BIOS bug 8254 timer not connected to IO-APIC
.263000] ...trying to set up timer (IRQ0) through the 8259A ... Failed!
.263000] ...trying to set up timer as Virtual Wire IRQ... Failed!
.263000] ...trying to set up timer as ExtINT IRQ... Failed :(.
.372000] Kernal panic - not syncing: IO-APIC + timer doesn't work!

As I said, this is from 5.10, when using 6.06 I get just the last line (if I remember correctly). I will post my findings in my thread so that it's coverd there as well.

I hope this helps.

---

