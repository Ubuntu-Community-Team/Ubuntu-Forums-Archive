---
title: "Cannot boot into installation screen."
date: 2012-05-15
forum: Installation &amp; Upgrades
---

### Post by zhangchi0116 on 2012-05-15
Have been trying in the past month. Used to install Ubuntu onto my notebook and netbook, nothing happened like this before.

Almost tried everything, xubuntu, ubuntu 32bit, ubuntu 64bit, even fedora 16 and openSuse 12.1. The problem should be the video card driver. But I have tried nomodeset, acpi=off, noapic, xforce vesa None of them are working.

Here is my hardware config:
CPU: i7 2600K
Motherboard: Asus P8Z77-Pro,
Video card: Zotac, nvidia 560Ti 1G

Hope anyone can give me some tips other than the above solutions. Thanks a lot.

---

### Post by efflandt on 2012-05-16
Are you trying to go directly to install, or booting a live system first?  Sometime in the distant past I had better luck doing "Try Ubuntu" first, and then installing from there.  You did not say what actually happened (blank screen? Did you wait long enough?).  It can take awhile to boot from CD or live/install iso on USB.

I did use nomodeset when booting 64-bit 12.04 live/install iso from USB stick, but found that I did not have to use nomodeset on the installed system (which for now is installed on a USB hard drive to try it out).  The live/install used nouveau drivers, and installed system automatically had nvidia drivers active. This was for desktop in my sig with NVIDIA GTX 550 Ti.

Strangely I did NOT have to use nomodset for 10.10,  I HAD to use nomodset for 11.10, and I do NOT have to use nomodset for 12.04.

64-bit 12.04 iso on USB does boot without any parameters on my Acer tablet PC, but that is a 1 GHz 2 core AMD with ATI graphics (Radeon HD 6250).

---

### Post by zhangchi0116 on 2012-05-18
Thanks a lot, efflandt. Sorry for the late reply, have been working late these days.

Two questions:
1.I did try ubuntu, install Ubuntu through wubi, and several other ways, and they all lead to a blank screen, keep flashing HDD led, no keyword led, no mouse power. It is like the whole procedure is freezing.
2. I tried to wait and did nothing during the install. But how long it normally should be? Especially your case with the nvidia 550 Ti?

Thank again, and look forward to the reply.

> **efflandt said:**
> Are you trying to go directly to install, or booting a live system first?  Sometime in the distant past I had better luck doing "Try Ubuntu" first, and then installing from there.  You did not say what actually happened (blank screen? Did you wait long enough?).  It can take awhile to boot from CD or live/install iso on USB.

I did use nomodeset when booting 64-bit 12.04 live/install iso from USB stick, but found that I did not have to use nomodeset on the installed system (which for now is installed on a USB hard drive to try it out).  The live/install used nouveau drivers, and installed system automatically had nvidia drivers active. This was for desktop in my sig with NVIDIA GTX 550 Ti.

Strangely I did NOT have to use nomodset for 10.10,  I HAD to use nomodset for 11.10, and I do NOT have to use nomodset for 12.04.

64-bit 12.04 iso on USB does boot without any parameters on my Acer tablet PC, but that is a 1 GHz 2 core AMD with ATI graphics (Radeon HD 6250).

---

### Post by darkod on 2012-05-18
Don't wait, use the nomodeset parameter to see if that will help get a working live desktop. Try the live mode first.

If that works, after you install you might need to use the parameter again on first boot to allow you to boot once and install the driver.

All the details are here:
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

---

### Post by zhangchi0116 on 2012-05-19
No lucky... I waited for about 20 mins and nothing happened.

The case is: After I click the try ubuntu with the nomodeset option, the screen will keep showing a flashing cursor at the upper left corner, after a while, keyboard and mouse were not functioning (no power for them at all). Has anyone seen this before?

> **darkod said:**
> Don't wait, use the nomodeset parameter to see if that will help get a working live desktop. Try the live mode first.

If that works, after you install you might need to use the parameter again on first boot to allow you to boot once and install the driver.

All the details are here:
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

---

### Post by slofroggy on 2012-05-28
I have the same problem. This doesn't work for me either.

My hardware configuration is

Motherboard: P8Z77-V (latest bios)
CPU: i7 3770
integrated video card

---

