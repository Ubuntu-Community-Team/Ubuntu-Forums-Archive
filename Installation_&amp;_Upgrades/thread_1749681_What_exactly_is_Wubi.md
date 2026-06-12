---
title: "What exactly is Wubi?"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by dugthemathguy on 2011-05-04
Hi I am wanting to put run Ubuntu on my WIndows & machine and noticed the option of installing wubi. I'm confused what wubi actually does:
is it basically an installer that handles the nitty gritty of installing a ubuntu partition so you can choose which OS to run?
or is it some kind of virtualization to run Ubuntu in Windows?
If its more like the latter, I'm wondering if there are performance consequences.
WHat I'm doing requires good performance and I just got a quad core with a sandy bridge i7 processor so I don't want to limit performance too much,
on the other hand I'm new to Ubuntu and Linux and so I don't want to have lots of technical problems :confused: that I don't understand that delay my work and reduce my general sanity.
So I could be OK with a small performance price if there was a significant chance I'd avoid stuff breaking.
Any advice would we very welcome
Doug

---

### Post by kansasnoob on 2011-05-04
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

[http://wubi.sourceforge.net/faq.php](http://wubi.sourceforge.net/faq.php)

> What is the performance?

The performance is identical to a standard installation, except for hard-disk access which is slightly slower than an installation to a dedicated partition. If your hard disk is very fragmented the performance will degenerate.


Any gotcha?

Hibernation is not supported under Wubi, moreover **[COLOR="Red"]Wubi filesystem is more vulnerable to hard-reboots (turning off the power) and power outages than a normal filesystem, so try to avoid unplugging the power.[/COLOR]** An Ubuntu installation to a dedicated partition provides a filesystem that is more robust and can better tolerate such events.


---

### Post by wilee-nilee on 2011-05-04
> **dugthemathguy said:**
> Hi I am wanting to put run Ubuntu on my WIndows & machine and noticed the option of installing wubi. I'm confused what wubi actually does:
is it basically an installer that handles the nitty gritty of installing a ubuntu partition so you can choose which OS to run?
or is it some kind of virtualization to run Ubuntu in Windows?
If its more like the latter, I'm wondering if there are performance consequences.
WHat I'm doing requires good performance and I just got a quad core with a sandy bridge i7 processor so I don't want to limit performance too much,
on the other hand I'm new to Ubuntu and Linux and so I don't want to have lots of technical problems :confused: that I don't understand that delay my work and reduce my general sanity.
So I could be OK with a small performance price if there was a significant chance I'd avoid stuff breaking.
Any advice would we very welcome
Doug

Wubi is a sort of virtual inside windows, it is basically a file in windows. You have the ubuntu option to boot to from the MS menu at boot, rather then the normal straight to windows if you have only one MS install.

It runs a little slower, but is actually a very good way of getting orientated with Ubuntu. You will not really recognise any speed difference I suspect it goes pretty smooth.

The original idea for wubi was to give people a chance of trying it out without actually doing a full partitioned dualboot. Theoretically it is a dual boot but different then a regular partitioned install. Some decide to go with the partitioned boot after a while, and there is a thread on how to transfer your wubi setup to a regular partition. Here is a link that may be more easily understood.
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

