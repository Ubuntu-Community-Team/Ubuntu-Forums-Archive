---
title: "dual boot from usb stick"
date: 2008-10-29
forum: Installation &amp; Upgrades
---

### Post by jamaas on 2008-10-29
Hi all,

Quick one, is it possible to have both a bootable version of ubuntu an a version of xp on the same usb stick and be able to choose which to boot?

Thanks

Jim

---

### Post by caljohnsmith on 2008-10-29
Assuming your USB stick is large enough, I think it should work just fine. Just install Win XP first and after that Ubuntu so that Ubuntu will set up Grub to boot both OSes. To do that though you will need to click on the "advanced" button in the final stage of the Ubuntu installer, and tell Grub to install to /dev/sdb or whichever is your USB stick. Just make sure you don't use (hd0) or /dev/sda, because that would install Grub to the MBR (Master Boot Record) of the computer's internal HDD. 

Are you going to use that USB drive in another computer? Because then you would want to install the Ubuntu Live CD instead I would think so that the install would be hardware-indepedent.

---

### Post by snowpine on 2008-10-29
> **caljohnsmith said:**
> Are you going to use that USB drive in another computer? Because then you would want to install the Ubuntu Live CD instead I would think so that the install would be hardware-indepedent.

This is not true; Ubuntu auto-detects hardware equally well whether you're running it as a Live USB or a full USB install.

I do not think the same can be said of Windows. I imagine you will run into driver problems if your intent is to use the USB stick on multiple computers. Can't say as I've ever tried it though; sounds like a fun project and good luck!

---

### Post by caljohnsmith on 2008-10-29
> **snowpine said:**
> This is not true; Ubuntu auto-detects hardware equally well whether you're running it as a Live USB or a full USB install.

I do not think the same can be said of Windows. I imagine you will run into driver problems if your intent is to use the USB stick on multiple computers. Can't say as I've ever tried it though; sounds like a fun project and good luck!
To my knowledge, once you do a full uninstall and configure Ubuntu for whichever computer you are using, then plugging that Ubuntu into another computer will not make it automatically detect the hardware changes and adjust accordingly. For instance, my Ubuntu is configured to use my particular monitor, sound card, wifi card, etc, and if I take my HDD and plug it into another computer, then to my knowledge Ubuntu won't automatically adjust to the new hardware. On the other hand, a Live USB would try to adjust to the specific hardware present every time you boot it though, just like the Live CD. Or at least it would always use the same defaults (like the Live CD) so that you can always configure the monitor, sound card, wifi card, etc. manually. That's all I was saying, but please correct me if I'm wrong. :)

---

### Post by C.S.Cameron on 2008-10-29
I think windows only works on the computer it was installed on.
I have not had success getting windows setu to see a flash drive.

---

### Post by snowpine on 2008-10-29
> **caljohnsmith said:**
> To my knowledge, once you do a full uninstall and configure Ubuntu for whichever computer you are using, then plugging that Ubuntu into another computer will not make it automatically detect the hardware changes and adjust accordingly. For instance, my Ubuntu is configured to use my particular monitor, sound card, wifi card, etc, and if I take my HDD and plug it into another computer, then to my knowledge Ubuntu won't automatically adjust to the new hardware. On the other hand, a Live USB would try to adjust to the specific hardware present every time you boot it though, just like the Live CD. Or at least it would always use the same defaults (like the Live CD) so that you can always configure the monitor, sound card, wifi card, etc. manually. That's all I was saying, but please correct me if I'm wrong. :)

Some linux distros (such as Gentoo) are compiled specifically for your hardware. Ubuntu is not one of them. My Ubuntu USB stick (a full install, not a Live USB) has worked on every computer I've tried it on...

You are correct however that certain wireless adaptors, video cards, etc. are not supported by Ubuntu out-of-the-box, so there is no guarantee your Ubuntu-on-USB would be 100% compatible with every system. However, if there was an incompatibility, it would rear its ugly head regardless of whether you were using a live USB or a full USB install. Of course, with a full USB install, you could download the necessary drivers so that it would then work the next time you used that same hardware. :)

(edit) I actually carry around a USB wireless adaptor that I know works with my USB stick. That way, I am virtually guaranteed a working wireless connection... unless of course the computer only has one USB port!!!

---

