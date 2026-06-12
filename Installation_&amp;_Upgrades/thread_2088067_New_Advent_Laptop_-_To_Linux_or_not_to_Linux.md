---
title: "New Advent Laptop - To Linux or not to Linux?"
date: 2012-11-25
forum: Installation &amp; Upgrades
---

### Post by GaryTheCat on 2012-11-25
Hello

I'm thinking of buying my girlfriend a new laptop for her birthday.  She's not the most computer literate person in the world but seemed to do OK with Xubuntu on an old laptop.

I've just been to the local PC shop to look at Windows 8 (as I've not seen it before) and to be honest, it looks like it would just confuse her - it made me feel a bit ill looking at the UI and I think any reasonable human being would just want to get rid of it.

The machine I was thinking of is [https://www.adventcomputers.co.uk/product/advent-monza-t100-156-laptop]("https://www.adventcomputers.co.uk/product/advent-monza-t100-156-laptop")

It looks to have a reasonable spec (6 Gb RAM) for a very reasonable price.  Looking at the specs, is there anything that leaps out saying "Ubuntu won't work well on this?"

I've searched the forums and the only thing that may be an issue is the webcam - although I'm not sure that would get any use anyway.

Any help / pointers / advice is most welcome.

Many thanks

G

---

### Post by GaryTheCat on 2012-11-25
Also, I can't tell if it's 32 or 64 bit - does that matter?

---

### Post by Isamu715 on 2012-11-25
This laptop is definitely 64-bit(and it does matter). Nothing in particular seems to be not-compatible with Ubuntu. Integrated Intel GPUs work well and don't require proprietary drivers, so that one's fine. The manufacturer doesn't state what wireless chipset is this laptop using but most are compatible with Ubuntu nowadays. The greatest problem which may occur is secure boot which is enabled by default on all Windows 8 PCs, whether a switch to disable it is present in BIOS is completely up to the manufacturer so you should prioritize finding that out as even if all the hardware is compatible it's no use if Ubuntu simply won't boot.

---

### Post by GaryTheCat on 2012-11-25
Thanks for that. 

Is there an easy way to find out whether secure boot can be disabled in the BIOS? (I guess the simplest option is to contact the manufacturer). 

If it has got secure boot, what will happen if I try to install Ubuntu? Will it not recognise one or other of the OSs or will it just become an expensive paperweight?

TIA 

Gary

---

### Post by Isamu715 on 2012-11-25
You'll need to contact the manufacturer or someone who has such a device.
There's no questioning if the secure boot is enabled or not. It definitely is, it's a prerequisite Microsoft has set for devices shipping with Windows 8. The question is whether it can be disabled. If it is enabled your Ubuntu LiveCD, USB drive or whatever will not boot. You will not even be able to try to install it.

---

### Post by GaryTheCat on 2012-11-25
Thanks again. Is there any way to completely remove windows 8 and then install Ubuntu? Sorry for the repeated questions. (May have been easier if I asked all of this in one post)

---

### Post by Isamu715 on 2012-11-25
Yes, with secure boot disabled you'll be able to install Ubuntu the usual way with the ability to wipe the hard drive clean.

---

### Post by GaryTheCat on 2012-11-25
Thanks. I'll have a look and try to find out how to completely remove windows 8. It gives me a headache just looking at it!

---

### Post by GaryTheCat on 2012-11-26
It seems it UEFI can be disabled - looks like it's time to go shopping.

I'll mark this thread as solved if I get the installation to work without any problems.

Thanks again :)

---

