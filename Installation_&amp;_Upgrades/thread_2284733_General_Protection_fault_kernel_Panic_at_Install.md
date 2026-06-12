---
title: "General Protection fault kernel Panic at Install"
date: 2015-07-01
forum: Installation &amp; Upgrades
---

### Post by victor63 on 2015-07-01
Hello
I am trying to clean install Ubuntu Studio 14.04 on my acer aspire m5641 but:
- getting to "Try Ubuntu before installing" takes ages (10 to 30 minutes, if it actually happens!)
- Openning and going through the steps of "install Ubuntu Studio 14.04" takes even longer, it did freeze once and seem to have deleted Windows (but I don't mind about that)
- I finaly got to "install now" and 5 minutes later, I got this screen:
[IMG]http://s23.postimg.org/6eszfqevv/photo_2.jpg[/IMG]

What does it mean? What do you think is going wrong with the install (it's as slow with Ubuntu 14.04 on another USB stick)?

---

### Post by victor63 on 2015-07-02
Ok, I have managed to install Ubuntu Studio14.04 by not connecting to the internet and not checking both "install third party programmes".
Now my keyboard and mouse become unresponsive after a while, but only those usb because my wireless usb thing keeps working. How can I fix this? does it have a link to my issue above?

---

### Post by dino99 on 2015-07-02
thats a good news you have managed to install it :p
about the kernel panic first met, it can be many things, like the iso quality (md5sum borked), or the bios/uefi applying a too low ram voltage (i have had that problem myself: need to set the real ram voltage into the bios instead of the 'auto' default setting (available via manual cpu frequency), or ...

have rebooted after the installation ? and checked about possible updates ?
about the keyboard unresponsive and the other troubl(s), try to glance at the logs to find the reason(s) (/var/log/dmesg, into /home: xorg.0.log)

---

### Post by victor63 on 2015-07-02
Thanks for your response! I've rebooted, but had to force shutdown before updating anything because mouse and keyboard became unresponsive after 1 or 2 minutes. 

Luckily I've managed to reboot and get enough time with keyboard and mouse to update softwares, check if i needed additional drivers (none required), but after about 10-15 minutes both keyboard and mouse just stopped working, the led under my mouse stays on until I try unplugging it and plug it again.

But now, I've rebooted and clicked "install language support", it failed reporting an error with aptdemon, and now all icons, bars etc.. have disappeared, leaving me only with the background image and my cursor (that I can move, yeah!...)

I am going to try to access the logs.

---

### Post by victor63 on 2015-07-02
reboot: keyboard and mouse unresponsive from the beginning and stay this way (everything else seem to be going well in the background)
reboot: screen stays in power saving mode after quickly showing the DELL logo screen. 
reboot: GRUB gives me some options, I don't know what to do, so i boot into "ubuntu" (not ubuntu low latency), mouse and keyboard become unresponsive as soon as the graphical environment is loading. After a few minutes, mouse becomes responsive again, so I click on File system manager, and suddenly He (my mouse) stops again.

---

### Post by tgalati4 on 2015-07-02
It's possible that the low-latency kernel used in Ubuntu Studio does not play well with an Acer Aspire--that would be consistent with an unresponsive mouse and keyboard.  Try the standard version of Lubuntu or Xubuntu or Ubuntu MATE.

How much RAM on this machine?

---

### Post by victor63 on 2015-07-20
Hello again, sorry for the late response. 

Thanks tgalati4, you were right. Although my Acer Aspire has got 4GB ram, it really didn't like Ubuntu Studio 14.04, nor did it want to install from my startup disk of the standard Ubuntu 14.04 (I would always get stuck with a "Busy box initframs" monologue). 
Ubuntu Studio even started to behave more and more out of the ordinary, it was a firework of weird bugs. 

I have now installed Xubuntu without any issue, it seems to run smoothly for now. I am going to try to turn it into a audio-visual workstation as I originally intended, just without low-latency kernel. ([https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)).

Thanks a lot for the hints!

---

