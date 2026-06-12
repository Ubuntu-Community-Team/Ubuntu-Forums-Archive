---
title: "hey guys please help im new to linux"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by jegannon on 2010-06-14
ok i might just be an idiot and be missing something but please help im new to ubuntu and really want to get into it.
i am installing on an hp pavilion a712n with 2.0ghz processor and i believe 2 gb memory
i have downloaded the iso on a cd and a dvd both failed( and i did write it at under 4x speed) i go through the entire install process fine and the restart box comes up i hit that and then it resart a few command prompt things flash then ubuntu appears to me loading with the five dots the my cursor shows up on a black screen the my monitor says it is going to sleep then it starts all over
please help
oh and i wrote all the cd's and dvd on a MacBook
thank you soo much in advance

---

### Post by quixote on 2010-06-17
Well, that's a new one for me.  Sounds like the power manager isn't interacting right with your system.  If you're up for trying yet another install, try hitting F6 for "Other options" at the bottom of one of the screens when you do it.  I don't remember what they all are, but try "noapic", "nolapic".  If there's anything to install without "ACPI" then select that as well.  ACPI does the power management, and in general you want it.  But if it boots without it, then you know where the problem is, and we can try to get it working.

---

### Post by GregBrannon on 2010-06-17
If the OP was able to boot using another method - e.g. using a boot disk or CD - isn't there a log that can be inspected to determine why his startup fails and reboots?

---

### Post by wilee-nilee on 2010-06-17
> **jegannon said:**
> ok i might just be an idiot and be missing something but please help im new to ubuntu and really want to get into it.
i am installing on an hp pavilion a712n with 2.0ghz processor and i believe 2 gb memory
i have downloaded the iso on a cd and a dvd both failed( and i did write it at under 4x speed) i go through the entire install process fine and the restart box comes up i hit that and then it resart a few command prompt things flash then ubuntu appears to me loading with the five dots the my cursor shows up on a black screen the my monitor says it is going to sleep then it starts all over
please help
oh and i wrote all the cd's and dvd on a MacBook
thank you soo much in advance

Are you trying to install in a live windows environment=wubi or are you booting the cd?

---

### Post by wojox on 2010-06-17
What kind of Graphics card/chip do you have?

---

### Post by mickwombat on 2010-06-17
Sorry if this sounds patronising, but did you take the CD out when you rebooted?

---

