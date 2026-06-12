---
title: "New GeForce 9500, Won't Boot"
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by metalxxxfuhrer on 2010-04-21
I just bought a new PNY GeForce 9500 GT and when it's installed my computer won't boot. Will not even pull up BIOS, nothing. When I take it out everything works fine.
I'm currently running Ubuntu 9.10, with a MSI P7N Platinum mother board and an Intel Core 2 Quad Processor. I'm hoping its not DOA, so please let me know if i'm missing something. Thanks.

---

### Post by kieran_uk on 2010-04-21
> **metalxxxfuhrer said:**
> I just bought a new PNY GeForce 9500 GT and when it's installed my computer won't boot. Will not even pull up BIOS, nothing. When I take it out everything works fine.
I'm currently running Ubuntu 9.10, with a MSI P7N Platinum mother board and an Intel Core 2 Quad Processor. I'm hoping its not DOA, so please let me know if i'm missing something. Thanks.

Sounds like a faulty card to me, do the warranty thing and send it back pronto!! :)

Regards, Kieran.

---

### Post by acej1995 on 2010-04-21
I think I have the same problem not sure what you ment.  I have a NVidia GeForce 9400, It works perfect with my windows 7 side, but when I use Ubuntu and get on my game, it doesn't detect it through ubuntu, why is this?

---

### Post by AnonCat on 2010-04-21
Even though you probably have the onboard video turned off in the bios, there could still be a conflict between it and the new video card.  This happened to me and I wasn't able to fix the problem until I blacklisted my onboard graphics hardware.  For some reason, the card will work in Windows without having to do anything about the onboard video, but Ubuntu requires the onboard to be blacklisted.  There might be a jumper on your motherboard that kills the onboard video that you can pull.

---

### Post by acej1995 on 2010-04-21
> **AnonCat said:**
> Even though you probably have the onboard video turned off in the bios, there could still be a conflict between it and the new video card.  This happened to me and I wasn't able to fix the problem until I blacklisted my onboard graphics hardware.  For some reason, the card will work in Windows without having to do anything about the onboard video, but Ubuntu requires the onboard to be blacklisted.  There might be a jumper on your motherboard that kills the onboard video that you can pull.

How am I able to blacklist the onboard graphics hardware?

---

### Post by metalxxxfuhrer on 2010-04-22
So I got a new card and now it boots up. Only problem is the only resolution I can get is 1440x900, which is the size of my old monitor. I've tried updating the NVIDIA drivers, and i'm still to new with linux to know any other ways, like modifying the xorg.config file by hand.

---

