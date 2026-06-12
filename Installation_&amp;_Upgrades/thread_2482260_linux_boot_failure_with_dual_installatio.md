---
title: "linux boot failure with dual installatio"
date: 2022-12-26
forum: Installation &amp; Upgrades
---

### Post by ksso on 2022-12-26
Hi,

I have installed xubuntu alongside with w11 in a hp AMD Ryzen 5 5500U with Radeon Graphics
Have tried automatic and manual installation
In both cases the installation was succesful and apparently the grub has the two options to rub xubuntu and linux
however, *after* running windows again, the grub for linux and xubuntu *disappears *(access inmediatly to windows, also can not fin the option to deactivate fast boot for windows11)
I could access again linux with keyboard options but the original dual grub options doesnt appear again, no matter which kind of installation is done

that its, may be try fix grub, but for a non-developer, is not as easy

thank you very much

---

### Post by ubfan1 on 2022-12-26
The Windows "fast startup" is pretty well buried:  Settings/Power & sleep/Choose What the Power Button does/Change Settings that are currently unavailable   Then you can uncheck the fast startup.  But that's for Windows 10, could be different with Windows 11.

---

### Post by yancek on 2022-12-26
Follow the suggestions in post 2 to see if that helps.  Windows often will set itself to first boot in the BIOS firmware so you would need to set ubuntu to first boot priority there.

---

### Post by ksso on 2022-12-26
The power button option never appeared... (w11)
right now I'm just using xubuntu, but I wanted to post that issue
Thank you!

---

### Post by ubfan1 on 2022-12-26
From Google I see: Press the Win key  and click on the power button icon in the Start menu. You will see that  hibernate option is available in the start menu now. If you want to  disable the hibernate feature, **retrace the above steps and uncheck the Hibernate checkbox**. Then click on the Save changes button to disable the feature.

---

### Post by tea for one on 2022-12-27
> **ksso said:**
> The power button option never appeared... (w11)
There are many websites with info about Windows 11 and Fast Start Up/Hibernation.
For example [https://www.makeuseof.com/windows-11-turn-on-or-off-fast-startup/](https://www.makeuseof.com/windows-11-turn-on-or-off-fast-startup/)

---

