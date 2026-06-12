---
title: "Ubuntu does not support the graphics card gtx960m"
date: 2017-04-19
forum: Installation &amp; Upgrades
---

### Post by alijk102 on 2017-04-19
Hi
I want to report a problem,I have a gaming laptop and want to install Ubuntu in that but Ubuntu is not working for install so I search a bout this problem so hard and I think its because of graphic card its gtx 960m
when I try to install Ubuntu and boot with bootable usb and select install Ubuntu its stop in logo you can see the logs in the pictures.
my laptop is GE62 6QD without ssd [https://www.msi.com/Laptop/GE62-6QD-Apache-Pro.html](https://www.msi.com/Laptop/GE62-6QD-Apache-Pro.html)
intel 6700HQ
GTX 960m 4GB DDR5
Intel(R) HD Graphics 530
16GB RAM DDR4
anyone can help me?
[ATTACH=CONFIG]274632[/ATTACH]   [ATTACH=CONFIG]274633[/ATTACH]   [ATTACH=CONFIG]274635[/ATTACH]

---

### Post by wildmanne39 on 2017-04-19
*Thread moved to **Installation & Upgrades**.*

You are wanting help to fix this issue correct and not just report it?

---

### Post by Bucky Ball on 2017-04-19
Boot to your BIOS and try switching off the internal graphics (the Intel HD) so it picks up only the GTX card. Ubuntu shouldn't have an issue with the GTX 960m (my wife's machine is running one and we did nothing, just installed Ubuntu).

---

### Post by alijk102 on 2017-04-19
I can't help to fix that just want report

---

### Post by alijk102 on 2017-04-19
> **Bucky Ball said:**
> Boot to your BIOS and try switching off the internal graphics (the Intel HD) so it picks up only the GTX card. Ubuntu shouldn't have an issue with the GTX 960m (my wife's machine is running one and we did nothing, just installed Ubuntu).
I can't disable graphic card there isn't  any similar option

---

### Post by deadflowr on 2017-04-19
> **alijk102 said:**
> I can't help to fix that just want report

Report it to the proper places.
Please read:
[https://ubuntuforums.org/showthread.php?t=1011078]("https://ubuntuforums.org/showthread.php?t=1011078")

We don't have anything to do with bugs.
And developers rarely, if ever, read random threads/posts in the forums.
(or randomly read forum threads/posts)

---

### Post by mdavidanderson on 2017-04-19
I upgraded the other night to 17.04, and was left with a computer that would only boot into recovery mode. I have an ASUS ZX50V with an nvidia gtx 960m processor, and found a good work around. 

First add the nomodeset to grub to hopefully boot up....followed the nomodeset instructions here: [https://ubuntuforums.org/showthread.php?t=1613132](https://ubuntuforums.org/showthread.php?t=1613132)

Secondly, I added the proprietary drivers repository with:
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update

Thirdly, I opened up the Additional Drivers tab in Software & Updates Settings. I then chose the proprietary nvidia 375.89 driver. 

Fourthly, removed nomodeset leaving just "quiet splash" from the grub file along with an update-grub. Restarted. And booted up normally.

---

