---
title: "apic problem"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by tromort on 2007-06-28
i wanted to install unbuntu next to my windows xp. so i downloaded the ubuntu 7.04 .iso file and burnt it on a cd-rom. 
when i reboot i see the ubuntu screen and select start/install ubuntu. after installing some parts i get the following error: 

Mp-bios bug: 8254 timer not connected to IO-APIC
kernel panic - not syncing: IO-APIC+timet doesn't work! boot with apic=debug and send report.
then try booting with the 'noapic' option.
:(
i checked my bios for any apic option but couldn't find one.
can anyone help to solve this?

i am useing:
 -windows xp (home) sp2
-AMD 64 X2 4200+

---

### Post by Drantral on 2007-06-28
hey tromort,

   I'm still new at linux, but i'll share something that worked for me with the apic issue. I currently have an Asus M2N4-SLI board that is plagued with this apic issue and after frantic research, i tried a variation of the solution found at [http://vip.asus.com/forum/view.aspx?id=20070407051536417&board_id=1&model=M2N4-SLI&page=1&SLanguage=en-us]("http://vip.asus.com/forum/view.aspx?id=20070407051536417&board_id=1&model=M2N4-SLI&page=1&SLanguage=en-us") and what worked for me was to get to install, hit F6 at the ubuntu boot select window from the livecd, in the options add "pci=noirq" (no quotes of course), and remove "quiet", some reason the quiet option would cause my system to still error out if left in. Hope that helps out.

---

### Post by tromort on 2007-06-28
i googled a bit and also found that about hitting F6 and enter things like pci=noirq but i never see a screen with ubuntu boot select.. or a other place/option to enter stuff like that.
thx for trying to help me

---

### Post by Drantral on 2007-06-28
the place you would hit F6 is going to be the same screen where you choose to "start or install ubuntu", "start ubuntu in safe graphics mode", etc. just on this screen hit F6, which is listed at the bottom said screen for other options, this will popup for lack of a better term, a command line, arrow right and it will start listing; ro, quiet, splash, here you should be able to apply the options i listed above.

---

### Post by tromort on 2007-06-28
thx! going to try this tomorrow cuz its already late now, i hope i works:p

---

### Post by tromort on 2007-06-29
i worked! i just had to enter noapic nolapic and then it worked :p (using ubuntu right now)

---

### Post by yellerKat on 2007-06-29
What's worked for **me** now on a M2N4-SLI is **ALL** of the following:

noapic
nolapic
acpi=noirq
pci=noirq
irqpoll (this may be redundant)

Thanks Drantral for the heads-up on removing the quiet option!

---

### Post by masteryurez on 2007-07-14
> **yellerKat said:**
> What's worked for **me** now on a M2N4-SLI is **ALL** of the following:

noapic
nolapic
acpi=noirq
pci=noirq
irqpoll (this may be redundant)

Thanks Drantral for the heads-up on removing the quiet option!


I tried to install Ubuntu on my brand new pc and i booted up Ubuntu 7.04 to the 
start screen. Hit F6 and wrote "noapic" without quote and Ubuntu booted up normally.
(If i don't write noapic the live-cd doesn't work). Anyway, I installed Ubuntu normally 
from Live-cd and I restarted my computer. 
But after GRUB has loaded my computer says this: 
```

Starting up ...
[   17.114789] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   17.293510] Kernel panic - not syncing: IO-APIC + timer doesn't work! 
Boot with apic=debug and send a report. Then try booting with the 'noapic' option
[   17.293543]

```...and I am back to square one again. I don't know what the problem is. 
Please help me.. It's easy to bootup Ubuntu but how do I do when I have restarted
my computer? I know that if I only boot up Ubuntu one time I can shut down the noapic
service but how do I boot up for the first time and get around the noapic option?

Please help me..

This is exactly how my pc looks like:
Motherboard: Gigabyte GA-M57SLI-S4 with socket AM2
RAM: 1 GiB 800 Mhz PC6400
CPU: AMD AM2 X2 4600+
Graphic: GeForce 7600GS 512 MiB PCI-Express

I hope someone can help me..

---

### Post by masteryurez on 2007-07-14
I have figured it out what the problem was I i have written a guide for it..
Just follow the guide and everything should work for you..

[http://ubuntuforums.org/showthread.php?t=500884&highlight=noapic](http://ubuntuforums.org/showthread.php?t=500884&highlight=noapic)

---

### Post by Matt 6:27 on 2007-07-17
Masteryurez, I'm looking to build a system with essentially the same specs as yours.  Other than the noapic problem listed above, how has your system performed?  I'm particularly interested in the compatibility of the GIGABYTE M57SLI-S4 and your video card.  Any guidance would be much appreciated!

---

### Post by masteryurez on 2007-07-18
> **Matt 6:27 said:**
> Masteryurez, I'm looking to build a system with essentially the same specs as yours.  Other than the noapic problem listed above, how has your system performed?  I'm particularly interested in the compatibility of the GIGABYTE M57SLI-S4 and your video card.  Any guidance would be much appreciated!


My system works as always, perfect. If you just have get passed the APIC-problem everything is working perfectly.. My computer gets 21385 points in 3DMark 2001 if you want to know...

---

### Post by Matt 6:27 on 2007-07-18
Most excellent.  Thank you!

---

