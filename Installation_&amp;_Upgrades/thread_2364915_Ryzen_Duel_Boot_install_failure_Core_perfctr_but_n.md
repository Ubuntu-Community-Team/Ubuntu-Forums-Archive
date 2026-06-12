---
title: "Ryzen Duel Boot install failure: Core perfctr but no contraints; unknown hardware!"
date: 2017-06-29
forum: Installation &amp; Upgrades
---

### Post by 9k2 on 2017-06-29
Hi,

I am unable to load either 16.04 or 17.04 via a bootable usb. Whenever Ubuntu attempts to load it gives me a:

"core perfctr but no constraints; unknown hardware!
nouveau 0000:29:00.0 priv: HUBO 00d054 000000007
nouveau 0000:29:00.0 DRM: failed to create kernel channel, -22"

message.

The machine works fine in W10, no idea why I am unable to get ubuntu onto it. Specs are: Ryzen 1700X, Nvidia 1080GTX, 16GB 3200Mhz DDR4, 512 M.2 SSD.

---

### Post by kurt18947 on 2017-06-29
I've read for for decent Ryzen support, you need to use the latest Linux kernel, 4.11 or something like that. Here is one set of directions that I think are sound.

[https://www.howtoforge.com/tutorial/how-to-upgrade-linux-kernel-in-ubuntu-1604-server/](https://www.howtoforge.com/tutorial/how-to-upgrade-linux-kernel-in-ubuntu-1604-server/)

I hope others more knowledge/experienced than I will jump in.

---

### Post by 9k2 on 2017-06-29
How can I do this when the Ubuntu live usb doesn't even load? I've tried downloading the latest daily dev and but I get the same exact issue. Is there an image which has 4.11?

---

### Post by kurt18947 on 2017-07-06
> **9k2 said:**
> How can I do this when the Ubuntu live usb doesn't even load? I've tried downloading the latest daily dev and but I get the same exact issue. Is there an image which has 4.11?

Good point. How are you creating the live USB? I've also noticed that some USB drives work better than others. I've had the best luck with plain vanilla devices, no extra features. My first choice is Micro Center branded USB3 flash drives. I guess they're beyond old school at this point but I don't think I've ever had a DVD fail to boot. They may take just short of forever but they do boot.

---

