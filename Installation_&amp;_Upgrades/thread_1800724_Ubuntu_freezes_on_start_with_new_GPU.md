---
title: "Ubuntu freezes on start with new GPU"
date: 2011-07-09
forum: Installation &amp; Upgrades
---

### Post by ThunderBubble on 2011-07-09
Hi all,
I recently upgraded my ubuntu desktop's video card.  All went well until I installed it's driver, when I rebooted I got stuck on a black screen with an unresponsive mouse just before the login screen.  Right now half of the time I get stuck on the black screen and the other half I can run 'buntu, with artifacts, for about a minute before it freezes and I have to force shut down

Thanks in advance,
TB

---

### Post by gordintoronto on 2011-07-09
Did you install the driver through Additional Drivers?

What version of Ubuntu? What was the old video card, and what is the new one?

---

### Post by ThunderBubble on 2011-07-09
This is the first video card I'm installing on the PC.  Specs:

TA 880GB+ motherboard
AMD Athlon II 250
XFX radeon HD 5750

Ubuntu version 10.10.  Sorry, forgot to include this in the first post.

---

### Post by ThunderBubble on 2011-07-09
I've now tried installing both from additional drivers and from the ATI website.  Both give me artifacts as soon as I get to the login screen and a lockup after about 30 seconds.

---

### Post by MAFoElffen on 2011-07-09
> **gordintoronto said:**
> 
What version of Ubuntu? [COLOR=Red]What was the old video card[/COLOR], and what is the new one?

> **ThunderBubble said:**
> This is the first video card I'm installing on the PC.  Specs:

[COLOR=Silver]<<BIOSTAR>>[/COLOR] TA 880GB+ motherboard
AMD Athlon II 250
XFX radeon HD 5750

Ubuntu version 10.10.  Sorry, forgot to include this in the first post.
@gordintoronto

Not jumping in... Just an observation and hint to speed things up for you, here is his original graphics on that motherboard: (So you two don't have to figure it out)
> 
ATI Hybrid Graphics Support (integrated/onboard)--
F7 is the native hotkey to switch between the AMD Chipset's integrated graphics processor and a discrete  GPU (ATI Radeon&#8482; HD 2400 Series ATI Radeon&#8482; HD 3400 Series)Have fun...

Edit-- Oh yes, almost forgot the "hint" part... The Catalyst driver has enough of a challenge going hybred with 2 chipsets... adding a third chipset?  Well, he's going to have to ensure that both onboard chipsets are disabled for the AMD Catalyst driver to see just the new card.  <<Gone now>>

---

### Post by ThunderBubble on 2011-07-09
Wait, BOTH onboard chipsets?  I was only aware of one, the radeon hd 4250.  Ubuntu worked fine with only that video card, before and after I installed the additional drivers.

---

### Post by ThunderBubble on 2011-07-11
Ideas, anyone?  This is driving me crazy.  I'm trying a clean install of 11.04 later, we'll see how that goes.

Edit:  Didn't work.  Still get artifacts and crashes after installing amd's driver.  No artifacts and stable but not much acceleration without the driver.

---

