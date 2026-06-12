---
title: "Jaunty 2.6.28-11-generic no cpuscaling"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by graysky on 2009-03-28
I posted this as a bug over at [launchpad](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350360) but that said, this is an old bug that is unfortunately [present in Intrepid](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/332846) as well.  

Anyway, I was hoping someone in here might see this thread and have an idea.

Basically, the problem is that upon logging into Gnome, the CPU Frequency Scaling Monitor tells me, "CPU frequency scaling unsupported.  You will not be able to modify the frequency of your machine. Your machine may be misconfigured or not have hardware support for CPU frequency scaling."  As a result, the processor is always at full speed.  This is in contrast to other LINUX distros in which cpu scaling works just fine without altering any BIOS settings (Debian/Lenny-amd64, Arch/Overlord-amd64).

---

### Post by novafluxx on 2009-03-28
This can't be good for my notebook ...:(

---

### Post by Polygon on 2009-03-28
it might just be a problem with your specific chipset, as i get cpuscaling with my laptop and jaunty

---

### Post by graysky on 2009-03-28
> **Polygon said:**
> it might just be a problem with your specific chipset, as i get cpuscaling with my laptop and jaunty

I don't think so... it's a P35 and scaling works with other distros as-is :(

---

### Post by Bossieman on 2009-03-28
No problem here with cpu-scaling. C2D P9500

---

### Post by graysky on 2009-03-30
I figured it out!  I took a clue from my /var/log/dmesg

```
[    4.633657] [Firmware Bug]: BIOS needs update for CPU frequency support
[    4.633718] ACPI Error (psloop-0136): Found unknown opcode 20 at AML address ffff88012d27c633 offset 4F, ignoring [20080926]
[    4.633722] ACPI Error (psloop-0136): Found unknown opcode 6F at AML address ffff88012d27c638 offset 54, ignoring [20080926]
[    4.633726] ACPI Error (psloop-0136): Found unknown opcode 20 at AML address ffff88012d27c63c offset 58, ignoring [20080926]
[    4.633729] ACPI Error (psloop-0136): Found unknown opcode 6F at AML address ffff88012d27c640 offset 5C, ignoring [20080926]
```

That line that reads, [color=red]Firmware Bug: BIOS needs update for CPU frequency support[/color] was really bugging me.  So I took a risk, d/l'ed the latest BIOS for my board, flashed, reset all my custom BIOS settings, and rebooted into my new kernel.  I'm now able to use acpi-cpufreq and scaling works smoothly :)

Thanks for all the advice.

---

