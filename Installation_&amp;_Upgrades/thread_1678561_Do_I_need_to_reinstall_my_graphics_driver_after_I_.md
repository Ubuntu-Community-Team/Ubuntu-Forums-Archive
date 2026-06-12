---
title: "Do I need to reinstall my graphics driver after I install ubuntu?"
date: 2011-01-30
forum: Installation &amp; Upgrades
---

### Post by ryanguy101 on 2011-01-30
I have a vaio with an ati radeon graphics card and windows 7. I wanted to try out ubuntu so I fully installed it (which I regret a little because I have to research alot for linux since I don't know much about). The thing I don't get is if you install another operating system does your computer keep the same drivers like the graphics card driver and stuff or do you have to go look for them again and reinstall them?

---

### Post by jocko on 2011-01-30
The different operating systems are completely independent from each other and use completely different drivers. Installing ubuntu will not in any way affect the software you have installed in windows, and ubuntu will not in any way be affected by whatever software you have in windows.
Ubuntu have a pre-installed open source graphics driver (named "radeon") for your graphics card, and if your graphics card is supported by ati's proprietary driver ("fglrx"), the hardware driver manager will automatically tell you about it and allow you to install it very easily.

---

### Post by ryanguy101 on 2011-01-30
Video driver for the ATI Radeon and FireGL graphics accelerators.

What is this? will it make my graphics better? I saw it on the open source center

---

### Post by jocko on 2011-01-31
> **ryanguy101 said:**
> Video driver for the ATI Radeon and FireGL graphics accelerators.

What is this? will it make my graphics better? I saw it on the open source center
Depends on what graphics card you have. If you have a supported card (radeon HD 2xxx and newer) the fglrx driver will work for you, and it performs better than the open source driver. 

Open up the hardware driver manager (System-->Administration-->Hardware Drivers). If it tells you there is a proprietary driver for your card, it is safe to install it, but if it does NOT tell you anything, you'll just break your graphics completely if you try to install it anyway...

If you are not sure despite this, why not tell us exactly what card you have?

---

### Post by thenickrulz on 2011-01-31
You probebly won't i didn't have too..

---

### Post by coffeecat on 2011-01-31
> **jocko said:**
> If it tells you there is a proprietary driver for your card, it is safe to install it, but if it does NOT tell you anything, you'll just break your graphics completely if you try to install it anyway...

@ryanguy101, before you install the proprietary driver that your system may prompt you with, check the following. Can you enable desktop effects? Can you play videos without any lagging? If yes to both then the default open source driver may be all you need. It is true that the proprietary driver offers superior performance but for many people this is only really needed for game playing. If you are not a game player and the default driver is working for you, I would strongly urge you not to install the proprietary driver. With some cards you will regret it. Believe me - I know this from bitter experience. It can sap your will to live. :wink:

Out of interest, which ATI video card do you have?

---

