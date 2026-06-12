---
title: "Trying to install Feisty on HP Pavilion DV6338se"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by LochNess on 2007-04-28
Hey all,

I'm trying to install Feisty on the above system, and when I boot the computer, the CD starts up, I see the Ubuntu logo, and then the text-mode stuff with the kernel starting to load things.  When the display shifts back to graphical mode, everything freezes up.

Does anyone have any suggestions?

It's got an AMD Turion dual core processor, NVIDIA GeForce Go 6150, 1GB RAM...

Is there some parameter I can pass to it when the system first boots that might get past this?

thanks!

---

### Post by geo_saleh on 2007-04-29
maybe if you add       noapic      in the boot command it will work

it happened with my laptop hp dv6284eu

---

### Post by LochNess on 2007-04-29
I'll give it a shot, thanks.

---

### Post by rapid_cl on 2007-05-01
Hi Guys.  I have a similar problem with my HP dv9205us same graphics card.  
[B]
How can use this  "noapic in the boot command"? [/B]

Thanks

---

### Post by LochNess on 2007-05-01
The noapic worked for me, now I just need to get the wireless working.

To use the noapic, what i did was, when you get boot with the CD and get the menu asking what you want to do, press F6 and enter 'noapic' on the end of the line that appears.

---

