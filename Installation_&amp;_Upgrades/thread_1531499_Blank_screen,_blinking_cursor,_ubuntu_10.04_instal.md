---
title: "Blank screen, blinking cursor, ubuntu 10.04 install (nomodeset no work)"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by 05sportstermadness on 2010-07-15
Im trying to install ubuntu 10.04 but to no avail.

after i get to menu and select install, blank screen with a cursor.

i have tried all the nomodeset theories but none work.

think anyone can help me out?


currenty windows 7
nvidia graphics card

---

### Post by viralmeme on 2010-07-15
> **05sportstermadness said:**
> after i get to menu and select install, blank screen with a cursor.

Dunno, try asking here .. [Ubuntu: NVIDIA driver]("http://www.jaredlog.com/?p=1148")

---

### Post by aspern on 2010-07-15
I have the exact same problem. 
Intel chipset and nvidia gpu, with win7 on the side.

---

### Post by 05sportstermadness on 2010-07-15
im a newbie, but if im right, it seems nomodeset disables graphics card?

so if i do that, what else would be stopping the install?

---

### Post by mörgæs on 2010-07-15
Please post the output of 

```
hwinfo --gfx
```

---

### Post by 05sportstermadness on 2010-07-16
loads some bars then eventually blanks on a blue screen with a grey bottom bar.

freezes there does nothing.


the way i input it was in the boot line

after the -- and before the --

---

### Post by mörgæs on 2010-07-16
The command must be given in a terminal.

---

### Post by 05sportstermadness on 2010-07-16
i dont have the linux operating system on my computer though.

unless im completely noob right now and you mean windows terminal?

---

### Post by mörgæs on 2010-07-16
Ohno, we don't want Windows to get in our way :-)

Can you run the command after booting with a live CD?

If 10.04 does not work, a 32 bit 9.10 is a good alternative.
[http://www.releases.ubuntu.com/](http://www.releases.ubuntu.com/)

---

