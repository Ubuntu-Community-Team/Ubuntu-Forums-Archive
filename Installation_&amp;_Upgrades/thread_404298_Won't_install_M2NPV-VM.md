---
title: "Won't install M2NPV-VM"
date: 2007-04-08
forum: Installation &amp; Upgrades
---

### Post by RichLouth on 2007-04-08
Hello,

When I try to install Ubuntu I get as far as "hda: cache flushes not supported" and then the system hangs without any activity. I have tried the kernel options nolapic, noapic, apci=off, fb=false, irqpoll in various combinations but every time it freezes at the same point.

I have performed the memory test on the CD and it has passed without errors.

I have tried various flavours of Ubuntu and they all fail in the same way. I have tried other distributions but they also fail to work. I have tested the HDD in a different machine and it works. I have fiddled with my bios settings and I have updated the bios of the mobo to the latest version. I have tried every configuration of RAM in the four slots.

The only other thing that I can see would be a problem in that the mobo has a 24 pin PCU connection but I am using a 20 pin connection. According to the manual though, it is OK for me to do this so long as I have greater than 300W. The ATX PSU I'm using has 550W.

I have:

Mobo: Asus M2NPV-VM Micro ATX (Socket AM2) PCI-Express DDR2 Motherboard
Processor: AMD Athlon 64 X2 Dual Core 4200+ 2.20GHz (Socket AM2)
Mem: Corsair 1GB DDR2 XMS2-6400C4 TwinX (2x512MB)
Graphics: GeForce 7100 GS (The problem exists with the onboard graphics too)

I am at a loss. I even tried installing Windows XP but that also fails quite early into the install. Does anyone have a similar experience? Any suggestions would be great:)

---

### Post by lqyjzmms on 2007-04-15
Hi RichLouth,

which Ubuntu release did you try? If you tried edgy (v6.10), it might be worth checking a current pre-release of feisty (the upcoming Ubuntu v7.04), e.g. the beta released on March 23rd [http://www.ubuntu.com/news/Ubuntu704Beta](http://www.ubuntu.com/news/Ubuntu704Beta) While v6.10 still uses Linux kernel v2.6.17, v7.04 comes with v2.6.20 at the moment. As every new kernel release includes new and updated drivers, and you are using current hardware, this might help.

Please keep us updated on your success, as I am considering to get the same motherboard for my next PC, which is of course supposed to run Ubuntu.

Best of luck

---

### Post by ArtInvent on 2007-04-23
I have the same mobo with no problems. You get what appears to be a hard drive error. If you have another HDD sitting around try that. This is the easiest thing to change. Are you using a SATA drive? I had a problem installing a beta of Feisty (partitioning problem, not a clean slate install) but had no problems with both 32 and 64 bit versions of edgy. If you were trying a version of Feisty try a version of Edgy.

---

### Post by RichLouth on 2007-06-07
Well after two months I finally discovered what the problem was.

I'd all but given up hope. Then I couple of days ago I decided to give it another stab.

Guess what it was that had me stumped for two months...

The IDE cable, supplied with the mobo, was knackered. I'd checked everything else but it never once occurred to me to check the cable! I quick swap with one I had lying around and now it all works. I'm a little peeved that something so simple has left my shiney new pc worthless for two months... but never mind. I'll move on.

Ubuntu works beautifully with my dual core amd! It brings a tear to the eye. Thanks Ubuntu

---

