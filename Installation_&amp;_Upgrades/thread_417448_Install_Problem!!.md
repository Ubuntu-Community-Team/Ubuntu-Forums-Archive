---
title: "Install Problem!!"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by thallium205 on 2007-04-21
After installing Ubuntu from the live CD, **I restart the computer and it goes to a black screen with a blinking cursor**!  I completely formatted my 320GB Maxtor hard drive and it is not working!  I have an Asus P5WD2 motherboard, and when it is at this black screen, even cntrl-alt-del does not restart the computer.  It acts as if it is completely frozen! I really need to get my computer up and running again and I was just wondering if someone was kind enough to help me!

Thanks in advance!

---

### Post by revoltism on 2007-04-21
It sounds like a graphic problem... try

```
sudo dpkg-reconfigure xserver-xorg
```

and follow the instructions

you should also install drivers for your graphic card if you haven't done so.

try the vesa drivers if you don't know or System > Admin > Proprietary drivers.

---

### Post by thallium205 on 2007-04-21
How am I suppose to install drivers if I have not even been able to run  Ubuntu from my hard drive?  While I am running it from the Live CD, it works and looks fine.  I have an ATI x550 POS graphics card.   Are you sure it could be a graphics driver?

---

### Post by AvixK7 on 2007-04-21
when you get to the black screen with the cursor, try entering the command that was just given to you.

---

### Post by thallium205 on 2007-04-21
I see.  I just tried that and I am unable to type anything.  Even ctr-alt-del will not restart the system.  All there is is a white blinking "-" on a black screen, and my computer is completely locked up.  Keep in mind this is the first reboot after the live cd install.

---

