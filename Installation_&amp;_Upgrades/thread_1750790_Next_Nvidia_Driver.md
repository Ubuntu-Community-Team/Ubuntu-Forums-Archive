---
title: "Next Nvidia Driver?"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by groovomata on 2011-05-05
I'm currently running 11.04 natty. Though in classic mode with no effects, because my laptop has an Nvidia GeForce Go 7300 graphics card, and unfortunately this card has been blacklisted due to a bug in the current 270.41.06 driver. Does anyone have any idea when the next driver release might be? I would really love to check Unity out.
Thanks,
Erik.

---

### Post by TrevP on 2011-05-06
It might be worth trying the experimental drivers. I'm using these with a nvidia 7200 card and they work brilliantly for me. Your system might still refuse to load Unity because your card is blacklisted but (I think) you can force Unity to load by adding the line UNITY_FORCE_START=1 in the /etc/environment file (you need to use sudo to do this). This works for me - but I don't think my card is blacklisted.

---

### Post by anthonyvo on 2011-05-06
So, let me get this straight? The issue that most people are having (unable to run Unity when they have Nvidia cards) is because some cards have been "blacklisted" in this new upgrade?

I have an Nvidia Quadro FX 1500 and can only run Classic but I get no effects (even though I had them with 10.10 after manually installing the driver.)

-Anthony

---

### Post by groovomata on 2011-05-08
> **TrevP said:**
> It might be worth trying the experimental drivers. I'm using these with a nvidia 7200 card and they work brilliantly for me. Your system might still refuse to load Unity because your card is blacklisted but (I think) you can force Unity to load by adding the line UNITY_FORCE_START=1 in the /etc/environment file (you need to use sudo to do this). This works for me - but I don't think my card is blacklisted.

I did this with the current 270.41.06 driver and Unity simply froze so I had to reboot. I was able to run Unity, sort of, with the 173 driver, though a number of things didn't work properly, such as I was unable to move windows and had no effects. 

Where are the experimental drivers located?

---

