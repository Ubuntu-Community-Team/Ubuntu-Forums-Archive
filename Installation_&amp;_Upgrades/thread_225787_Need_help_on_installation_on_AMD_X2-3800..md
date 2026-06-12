---
title: "Need help on installation on AMD X2-3800."
date: 2006-07-30
forum: Installation &amp; Upgrades
---

### Post by guoheng on 2006-07-30
When I boot from kubuntu 64, it hung after uncompressed the kernal. When I boot from kubuntu 32, it showed this message:

[4294672.027000]..MP_BIOS bug: 8254 timer not connected to IO-APIC kernel panic - not syncing : IO-APIC+timer doesn't work!

So I pressed F6 to add the option 'noapic'. I don't understand what this mean. Should this disable some features?

Anyway, with that option, both the 64bit and 32 bit live CD boot up. But there are 2 problems: 
1. there is no ineternet connection. I am connect to DSL through a router.
2. the display resolution is on 1024x768. My monitor is 1068x1050. I can not find a way to let the system configure to 1068x1050

My system configuration is:
AMD X2-3800
ASUS M2N-SLI DELUXE 
1 IDE HD and 1 SATA HD

I also tried to boot from DEBIAN 64bit. It boot with no 'kernel panic'. But it can not detect my network either. And Debian can not see my SATA HD. So I guess both Debian and Ubuntu installation don't deal well with the ASUS motherboard?

Has anyone succesfully installed on a AMD X2 machine?

---

### Post by tseliot on 2006-07-30
The CPU is not the problem. Maybe it's your motherboard.

Anyhow I suggest you to try this guide of mine:
[http://www.ubuntuforums.org/showthread.php?t=75281](http://www.ubuntuforums.org/showthread.php?t=75281)

Read the following part:
> [COLOR="Red"]a) If you haven't installed Ubuntu 32 bit yet...[/COLOR]

And try boot parameter 4 or 5. If they don't work try all the others.

---

### Post by guoheng on 2006-08-01
I found the solution for installation and the network issue

For the kernel panic issue, just boot with option 'noapic'

For the network issue, I found the solution from a suse usenet group. It turns out that I dual boot the machine. After shut down from windows , I need unplug the power cord of the computer off for a few second. Then re-plug the power cord and then boot to linux. After that the network issue is resolved.

Still have issue on the display at this point.

---

### Post by GuyveR800 on 2006-08-08
I installed Edgy Eft Knot 1 64-bit on a M2N-SLI motherboard. It worked without problems with BIOS 0202, but when I upgraded to 0304  I got the same error and needed to use NOAPIC as well.

Edgy seems to have fixed the dual-boot issue for the network though.

---

