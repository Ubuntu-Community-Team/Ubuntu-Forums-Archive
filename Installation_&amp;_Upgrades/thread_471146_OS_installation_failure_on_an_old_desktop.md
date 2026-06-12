---
title: "OS installation failure on an old desktop"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by One Quick Question on 2007-06-11
I had installed Kubuntu 6.06, I believe, on an old x86 desktop. It worked fine, but I decided to upgrade it to 7.04.  The upgrade went well as far as I could tell (i.e., no complaints).  I rebooted to load the new kernel and now the system won't get past the boot-up (on verbose mode) message after detecting the serial ports.

On my other computer, it looks similar to this:
```
[...cut...]
May  2 12:21:15 Wolgder kernel: [    0.729572] io scheduler cfq registered (default)
May  2 12:21:15 Wolgder kernel: [    0.729874] isapnp: Scanning for PnP cards...
May  2 12:21:15 Wolgder kernel: [    1.082807] isapnp: No Plug & Play device found
May  2 12:21:15 Wolgder kernel: [    1.108107] Real Time Clock Driver v1.12ac
May  2 12:21:15 Wolgder kernel: [    1.108162] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
May  2 12:21:15 Wolgder kernel: [    1.108276] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  2 12:21:15 Wolgder kernel: [    1.108992] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[...cut...]
```

So, thinking it was a problem with the upgrade skipping over 6.10 or something, I popped in a Kubuntu 7.04 cd and tried to boot from it.   Same problem.

However, a fairly recent release of Knoppix (sorry, don't know the version offhand. I could get it for you if it's needed) boots up fine.

The next thing in my messages log from my working machine is a check for mice, so I've removing the mouse, disabling PS/2 support from the BIOS, etc.  I've also disabling the serial ports from the BIOS, but it changes nothing.

Any ideas?

---

