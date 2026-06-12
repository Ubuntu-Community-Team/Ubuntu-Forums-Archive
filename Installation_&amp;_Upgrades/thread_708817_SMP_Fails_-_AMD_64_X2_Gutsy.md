---
title: "SMP Fails - AMD 64 X2 Gutsy"
date: 2008-02-26
forum: Installation &amp; Upgrades
---

### Post by chessiv on 2008-02-26
I setup this machine from the distro cd, worked great.  Shows both processors.  I use the same machine with the same setup cd and install to a usb drive and it only shows 1 processor

Feb 26 19:02:19 chuck-usb kernel: [    0.496000] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ stepping 02
Feb 26 19:02:19 chuck-usb kernel: [    0.496000] SMP alternatives: switching to SMP code
Feb 26 19:02:19 chuck-usb kernel: [    0.496000] Booting processor 1/1 eip 3000
Feb 26 19:02:19 chuck-usb kernel: [    5.152000] Not responding.
Feb 26 19:02:19 chuck-usb kernel: [    5.152000] Inquiring remote APIC #1...
Feb 26 19:02:19 chuck-usb kernel: [    5.152000] ... APIC #1 ID: 1000000
Feb 26 19:02:19 chuck-usb kernel: [    5.152000] ... APIC #1 VERSION: 80050010
Feb 26 19:02:19 chuck-usb kernel: [    5.152000] ... APIC #1 SPIV: ff
Feb 26 19:02:19 chuck-usb kernel: [    5.152000] CPU #1 not responding - cannot use it.
Feb 26 19:02:19 chuck-usb kernel: [    5.152000] Total of 1 processors activated (4292.60 BogoMIPS).
Feb 26 19:02:19 chuck-usb kernel: [    5.152000] ENABLING IO-APIC IRQs
Feb 26 19:02:19 chuck-usb kernel: [    5.152000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Feb 26 19:02:19 chuck-usb kernel: [    5.188000] Brought up 1 CPUs

Any ideas?  This seems to be a common issue.  I am running the generic core btw.

---

### Post by chessiv on 2008-02-27
A friend of mine tested this by plugging in a usb device and booting his machine and the same thing happened.  So somehow it appears to happen in relation to usb storage devices being used.

---

