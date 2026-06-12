---
title: "How to adjust GPU and graphic memory frequency?"
date: 2008-10-20
forum: Installation &amp; Upgrades
---

### Post by Markstar on 2008-10-20
Hi,
I would like to adjust the frequencies of my graphic card (ATI 4870) and were wondering how I could accomplish that. There are several tools for Windows (Overdrive, but I use AMD GPU Clock Tool v0.9.8 ), but how do I do it in Ubuntu?

Thank you in advance for your answers!

---

### Post by Hexagoon on 2008-10-20
This option should be available with the most recent fglrx, through the aticonfig utility. I don't think it is available in CCC Linux edition though.

---

### Post by Markstar on 2008-10-20
> **Hexagoon said:**
> This option should be available with the most recent fglrx, through the aticonfig utility. I don't think it is available in CCC Linux edition though.I do have the most recent driver version (8.10) installed. What do I do there? I tried:

```
markstar@HA06:~$ sudo aticonfig --lsp
Error: POWERplay is not supported on your hardware.
```

Why would Powerplay not be supported? 

Anyways, in Windows I can lower the frequencies to 200MHz (instead of 500, which saves about 40W). I have tried Overdrive, but this seems to be only for overclocking the card. :(

---

### Post by Markstar on 2008-10-21
So is it safe to assume that underclocking the graphic card is not possible in Ubuntu? :(

---

### Post by bartenst on 2008-11-07
Hmm, the graphic card of my notebook is a ATI HD 2600 and with Ubuntu Hardy I was able to use POWERplay with the ATI Catalyst (amdcccle). Unfortunately this feature is not available with the ATI Catalyst installed on Intrepid? How comes?

Would be nice to have this feature as my notebook's fan is now constantly running.

Greetings,
Dominik

---

### Post by miegiel on 2009-03-16
from : [http://ati.amd.com/products/powerplay/index.html](http://ati.amd.com/products/powerplay/index.html)
> ATI PowerPlay&#8482; technology is now available in ATI Radeon&#8482; HD 3800 Series desktop graphics processors, ATI Mobility Radeon&#8482; notebook graphics processors and Radeon&#8482; Express motherboard chipsets and may be enabled on certain ATI Partner products.

Doesn't list the ATI 4870

---

### Post by Ansraliant on 2009-05-15
Hi!. Have you tried to use aticonfig to set new clocks?.
Here's how I've changed my ATI HD 2600 from 600 to 650 GPU frequency.

First of all, you must enable Ati Overdrive feature writing the following:
Remember to write all the commands as root or sudo.
```

# aticonfig --od-enable

```
Check out what clocks do you have.
```

# aticonfig --adapter=0 --od-getclocks

```

You should see something like this:

```

dapter 0 - ATI Radeon HD 2600 Pro AGP
                            Core (MHz)    Memory (MHz)
           Current Clocks :    600           500
             Current Peak :    600           500
  Configurable Peak Range : [600-660]     [500-550]
                 GPU load :    0%

```

Now that you know your current clocks, write this:

```

# aticonfig --adapter=0 --od-setclocks=GPU,RAM

```

Where GPU, is the frequency you want for your GPU. And RAM the new Frequency for your RAM.

It worked for me, so it should work to you too.
Good Luck!

---

