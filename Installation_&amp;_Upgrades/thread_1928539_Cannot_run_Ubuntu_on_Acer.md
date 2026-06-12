---
title: "Cannot run Ubuntu on Acer"
date: 2012-02-20
forum: Installation &amp; Upgrades
---

### Post by advanirajesh on 2012-02-20
Hi

I am trying to run Ubuntu on Acer 4520 Amd 64 Machine. I downloaded ubuntu-11.10-desktop-amd64.iso and prepared a pendrive to boot the machine from.

**Problem:**
The machine prompts me to select from one of the options like "Run Ubuntu from USB" / "Install Ubuntu..." / etc.

I tried multiple times to run Ubuntu from USB, but clicking on it runs several lines of some code that I do not understand and after some time it just stops.

**History:**

The machine has various partitions. On D the previous version (I think 8.04) of Ubuntu was installed which stopped working at some point so I formatted the partition using Disk management utility in Windows recently. This might be causing some problem, not sure.

I would appreciate an early help in this regard.

Thanks,

Rajesh

---

### Post by Quackers on 2012-02-20
Welcome to UF :-)
Does the screen just go black? It could be a video problem. I believe it has a Nvidia graphics chip so it may be an idea to try the nomodeset boot option as described in the link below

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by advanirajesh on 2012-02-20
No. The screen does not go blank. Yes, it does have Nvidia Graphics. I tried nomodeset as you suggested, but it doesn't seem to help.

Thanks,

Rajesh

---

### Post by advanirajesh on 2012-02-20
The image of screen showing where the whole thing just stops:

[IMG]http://t.co/TBtFvJYQ[/IMG]

Awaiting an early help!

---

### Post by Quackers on 2012-02-20
No image :o

---

### Post by advanirajesh on 2012-02-20
Sorry, something went wrong. here is the link to image.

[http://t.co/TBtFvJYQ](http://t.co/TBtFvJYQ)

---

### Post by Quackers on 2012-02-20
That appears to be a kernel panic. Do your caps lock and num lock lights start flashing when the screen stops?
Unfortunately I'm not sure what may be causing that. It may be an idea to try a different version of Ubuntu as that will use a different kernel.

Alternately somebody else may have more ideas.

---

### Post by advanirajesh on 2012-02-20
Yes, the CAPS lock light starts flashing after the screen stops. I am not sure which version should I try. I guess, earlier the machine was on Ubuntu 8.04 or so.

---

### Post by Lisiano on 2012-02-20
Yep, indeed a kernel panic then. While I also don't have the slightest clue what might be wrong, but could you try booting with acpi=off or noapic?

---

