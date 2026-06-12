---
title: "Karmic won't load"
date: 2009-09-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Don1500 on 2009-09-12
I downloaded the karmic .iso, burned it to disk (at 16X) twice. 
When I try to boot to "Try", it loads to the second splash screen, goes black for a few seconds, then back to the second splash screen, repeat forever. tried loading all different ways, it did the same thing.

Any help?

---

### Post by VMC on 2009-09-12
> **Don1500 said:**
> I downloaded the karmic .iso, burned it to disk (at 16X) twice. 
When I try to boot to "Try", it loads to the second splash screen, goes black for a few seconds, then back to the second splash screen, repeat forever. tried loading all different ways, it did the same thing.

Any help?

Someone has a topic here with the exact same results. I have seen many similar results. You need to supply what video card your using. That's going to be the culprit.

---

### Post by Don1500 on 2009-09-12
> **VMC said:**
> Someone has a topic here with the exact same results. I have seen many similar results. You need to supply what video card your using. That's going to be the culprit.

output from lspci:
```
01:00.0 VGA compatible controller: ATI Technologies Inc RV630 [Radeon HD 2600XT]

```

I have Karmic Kubuntu running on another partition and it works fine. But I like Ubuntu better and want to see how 9.10 is going to be.

---

### Post by philinux on 2009-09-12
Should be burned at no more than 4x.

---

### Post by Don1500 on 2009-09-12
> **philinux said:**
> Should be burned at no more than 4x.

OK, Re-burned at 4X, no help. I don't think it has anything to do with the burn. 
Thanks, anyway.

---

### Post by taavikko on 2009-09-12
> **philinux said:**
> Should be burned at no more than 4x.

There's no need on newer hardware.
I've always used max speed and never had any issues with them.

The issue is with the software that liveCD contains, especially mesa.
which affects r600 chipsets and higher running ATI GPU's.

I would suggest that if must install, then retrieving older alpha4 and installing with it.
Though, when applying updates, the same issue will arise, due to updated mesa.

fix: install restricted fglrx drivers.

---

### Post by Don1500 on 2009-09-12
> **taavikko said:**
> There's no need on newer hardware.
I've always used max speed and never had any issues with them.

The issue is with the software that liveCD contains, especially mesa.
which affects r600 chipsets and higher running ATI GPU's.

I would suggest that if must install, then retrieving older alpha4 and installing with it.
Though, when applying updates, the same issue will arise, due to updated mesa.

fix: install restricted fglrx drivers.

How can I do that if I'm trying to run off the live CD?

Any response?

---

### Post by irate.turtle on 2009-09-13
Same problem for me when booting from USB.

```
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series

```

---

### Post by VMC on 2009-09-13
> **Don1500 said:**
> How can I do that if I'm trying to run off the live CD?

Any response?

Go [**here**]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") and read up on the fix. Then when you boot livecd, select F6 other options, add single to end of line, then boot selecting netroot from menu. Then you can apt-get or aptitude what you need.

---

