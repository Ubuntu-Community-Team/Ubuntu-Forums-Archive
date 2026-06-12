---
title: "Shutdown freezes with &quot;Starting Power-Off&quot;"
date: 2018-08-15
forum: Installation &amp; Upgrades
---

### Post by moooment on 2018-08-15
Bionic Beaver on a No-UEFI-but-still-BIOS-PC.

Restart works fine.

Mainboard is [http://www.asrock.com/mb/NVIDIA/M3N78D/](http://www.asrock.com/mb/NVIDIA/M3N78D/)

Grafics work fine but is old NVidia 7600 GT.

Everything works fine and fast (SSD) since more than 10 years.

Ideas?

---

### Post by mörgæs on 2018-08-16
HI, welcome to the fora.

It's often a good idea to post the complete hardware details though you have linked to the mainboard description.

Please copy ```
sudo lshw -sanitize > lshw.txt
``` and paste it to the command line, run it and post lshw.txt in CODE tags.

---

### Post by moooment on 2018-08-16
I understand that you want to have the full pic and not ask one thing after the other, which must be most annoying for you.
But that's much too much data, also enabling third persons fingerprinting my system.
If this is the condition of getting help I drop my question, maybe Ubuntu, no problem.
Thank you.

---

### Post by mörgæs on 2018-08-16
It's not a condition. You will see some people here begin from the detail and later move to the big picture. I tend to begin with the overview and then narrow down the problem to one or a few possible culprits. 

You don't have to drop the question. Just wait for some other posters to respond. 

As for your privacy: I value that a lot, too, and therefore I gave a command including *sanitize*. Try to see the results without the flag.

---

### Post by moooment on 2018-08-23
Somebody told me, it's an ACPI-problem, but couldn't go any further.
How to find out what device is freezing "Power Off"?

---

### Post by mörgæs on 2018-08-26
If you want to experiment without ACPI this thread, though old, is a good guide:

[https://ubuntuforums.org/showthread.php?t=1591381](https://ubuntuforums.org/showthread.php?t=1591381)

I have only tried Method 1.

Watch the CPU temperature if you begin playing with ACPI.

---

