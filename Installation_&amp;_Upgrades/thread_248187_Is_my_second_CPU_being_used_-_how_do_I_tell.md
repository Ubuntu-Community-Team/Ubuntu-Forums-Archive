---
title: "Is my second CPU being used? - how do I tell?"
date: 2006-08-31
forum: Installation &amp; Upgrades
---

### Post by blackdalek on 2006-08-31
I swapped the motherboard in this computer (a Pentium II 266) for a dual CPU Pentium III 650 board (an Intel L440GX+ server board).

After booting up again after swapping the board, I reconfigured the Xserver-Xorg thing for the new onboard video hardware and everything else seemed to be working fine.

But when I look at processor under Device Manager, I just see one processor listed with -
Vendor: Unknown
Device: Unknown
Status: Status
Bus Type: PNP
Device Type: processor
Capabilities: processor

...and when I look at the System Monitor/Resources tab, I just see one CPU under CPU History.

Shouldn't I see two CPUs in System Monitor? And two processors under the Device Manager? And is it normal for the Device Manager to display "Unknown" for the device and vendor of CPU?

Have I done something wrong? Are both CPUs being used? If not, what do I need to do?

---

### Post by NetworkGuy on 2006-08-31
You are probably using the 386 kernel.   That kernel only supports one processor.  To use the second processor load the 686-smp kernel.  

That kernel support multiple processors.

apt-get install linux-686-smp

---

### Post by blackdalek on 2006-09-01
> **NetworkGuy said:**
> You are probably using the 386 kernel.   That kernel only supports one processor.  To use the second processor load the 686-smp kernel.

Thanks! I will give that a go. :)

---

### Post by blackdalek on 2006-09-05
that fixed it!

---

