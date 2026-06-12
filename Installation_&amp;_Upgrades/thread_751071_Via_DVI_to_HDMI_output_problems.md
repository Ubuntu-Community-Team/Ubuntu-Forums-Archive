---
title: "Via DVI to HDMI output problems"
date: 2008-04-10
forum: Installation &amp; Upgrades
---

### Post by kingu on 2008-04-10
Hi

A friend of mine have some troubles with connection between his PC (used as a mediacenter) and his LG LCD tv. 
The PC consists of VIA EX15000G mainboard, so the graphics chip is a Unichrome Pro.

If we connect the TV the TV's HDMI port (using a DVI -> HDMI dongle), the boot screen of Hardy will show up nicely, but when the xserver attempts to start, the TV loose its signal and stays that way. I'll get a picture if I jump to a TTY. 
If we use a regular VGA cable (through a DVI -> VGA dongle), it starts the xserver. 

I do know that Hardy is still beta, but with Gutsy the xserver crashed.
I'll first be able to get logs and configurationsfiles on friday (the 12th).

Have anyone expirenced similar things, and possibly a solution?

---

### Post by Trollslayer on 2008-04-11
I've had the same with a Panasonic plasma.
The solution seems to be to boot with the VGA connection then fix the resolution to 1280x720 (including for MythTV is you are running that) then HDMI video works fine.

---

### Post by kingu on 2008-04-14
Thaks for the reply.

I'll try that when I'll get arround his house. 
However I guess that one will need to use the VGA connection every time one would like to boot the computer?

---

