---
title: "Installed Ubuntu, but im Getting a White Screen on Boot"
date: 2024-09-30
forum: Installation &amp; Upgrades
---

### Post by mercyjoyce on 2024-09-30
Hi everyone,
I recently installed Ubuntu 22.04 LTS on my laptop, which previously had no operating system. The installation process went smoothly, but when I try to boot up after installation, I&#8217;m met with a blank white screen. I decide to do a fresh ubuntu install, but i get the same blank white screen. Anyone have faced this issue before and any ideas on how to fix this?[[COLOR=#ffffff] white screen[/COLOR]]("https://whitescreen.vip/")

---

### Post by sudodus on 2024-09-30
Please tell us details about the hardware: In particular, what is your graphics chip or card? If nvidia, you should try to boot with the [boot option](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808) **[FONT=Courier New]nomodeset[/FONT]**.

It would help us understand your problem, if you download and run the **[FONT=Courier New]system-info[/FONT]** script. If I understand correctly, the computer can boot into working graphics from an installer USB drive, and you can manage the **[FONT=Courier New]system-info[/FONT]** script from there.

See the following link:

[github.com/UbuntuForums/system-info/](https://github.com/UbuntuForums/system-info/)

---

