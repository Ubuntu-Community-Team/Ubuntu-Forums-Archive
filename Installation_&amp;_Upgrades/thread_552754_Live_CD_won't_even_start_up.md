---
title: "Live CD won't even start up"
date: 2007-09-16
forum: Installation &amp; Upgrades
---

### Post by steventrouble on 2007-09-16
I burnt the CD exactly as the tut showed me to, did a checksum, and then put the disc in and nothing happened. I rebooted again and all it showed was what it always does. I didn't ask me if i wanted to boot, it just went to windows... what do i do?

---

### Post by Seisen on 2007-09-16
Do you have your BIOS set to boot the CD?

---

### Post by steventrouble on 2007-09-16
Yes:

Advanced BIOS Settings:

First boot: CD-ROM
Second boot: Hard Drive
Third boot: Disabled [none]

---

### Post by Pumalite on 2007-09-16
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by steventrouble on 2007-09-16
read it, did it, failed at it

checksum = 100%
My computer skills = not a noob
BIOS = perfect
CMOS = Anything here that may stop it from working?



I have ABIT Motherboard
Intel chipset
and NVidia Geforce 6600

is that important?

---

### Post by Pumalite on 2007-09-16
'I didn't ask me if i wanted to boot'

Why doesn't just boot?. Mine just boots. Doesn't ask me anything. Is this a special board or BIOS?

---

### Post by steventrouble on 2007-09-16
ummm... ABIT board... has some monitoring program called uguru

but... what do you mean special board or bios?

umm... Norton Ghost Recovery CD just boots for me, but not this...

---

### Post by Pumalite on 2007-09-16
ABIT board...you answered my question. What is uguru?
I think you have a P35 chipset...is that right?

---

### Post by steventrouble on 2007-09-16
yeah......

---

### Post by Pumalite on 2007-09-16
you should set the onboard SATA/IDE controller to AHCI and you'll be okay
I had some experience with P35 but I used GA-P35-DS3R and kernel version 2.6.22 and it run just fine after I configured it to AHCI

---

### Post by splintercellguy on 2007-09-16
Does the CD autorun work on Windows? Just checking to see if burned properly. If the CD drive isn't working so well for you, [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation) may help.

---

### Post by steventrouble on 2007-09-17
I did that before I installed windows... D= and i think i might actually have K95/35

---

### Post by steventrouble on 2007-09-17
> **steventrouble said:**
> I did that before I installed windows... D= and i think i might actually have K95/35
Oops, A17

---

