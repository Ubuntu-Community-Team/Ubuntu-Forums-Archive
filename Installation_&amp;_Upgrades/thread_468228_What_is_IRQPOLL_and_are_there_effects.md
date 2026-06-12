---
title: "What is IRQPOLL and are there effects?"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by MCSE_Crossover on 2007-06-08
I have to boot Ubuntu 7.04 using the kernel option of "irqpoll." It doesn't work otherwise. It just hangs.

My mobo is an Asus P5W DH with 2GB RAM and a dual core intel. I have an ATA DVD, 1 ATA HD, and 2 SATA HD's.

Everything seems to work fine as long as I have that option in there, but i'm just curious about what exactly it does. Can someone explain what that option is exactly and why it makes the system work?

Also, is using that switch have any adverse effects on the system? Does it slow anything down or make things not work quite the right way? Or does it not really matter.

I had this problem with 6.10 as well. Any reasons why? I'm attributing it to a kernel bug?

I appreciate it.

---

### Post by MCSE_Crossover on 2007-06-12
Bump. No one can explain what IRQPOLL is? I know people use it...no one can explain the significance?

---

### Post by drfelson on 2007-06-16
You probably noticed the output of dmesg that suggests irqpoll hurts performance: "Misrouted IRQ fixup and polling support enabled. This may significantly impact system performance." I'm at the same place; I don't know what affect it has either.

I did find a reference, _Linux Kernel in a Nutshell_, that explains what irqpoll does:

"irqpoll When an interrupt is not handled, search all known interrupt handlers for it. This is intended to get systems with badly broken firmware running."

I need to use irqpoll to boot an old 750Mhz P3 laptop. Otherwise it says nobody cared on irq 15, try irqpoll, and then it doesn't finish booting up.

I hope this helps.

---

### Post by lproven on 2007-07-07
> I need to use irqpoll to boot an old 750Mhz P3 laptop. Otherwise it says nobody cared on 
> irq 15, try irqpoll, and then it doesn't finish booting up.

That's exactly what happens to me on my old IBM Thinkpad i1200 series. However, while irqpoll worked with 6.06, it doesn't seem to work for me with 6.10 or 7.04. It does work on Xandros 4, though, and PC-BSD installs without a problem.

Really wish I could find a more permanent solution!

---

