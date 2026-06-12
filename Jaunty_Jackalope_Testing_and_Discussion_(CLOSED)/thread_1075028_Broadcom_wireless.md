---
title: "Broadcom wireless?"
date: 2009-02-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by XtremeGamer99 on 2009-02-19
Hello,

I've just installed Kubuntu 9.04 Alpha onto my laptop, and I was surprised to see that my wireless card was not working. I was surprised because when 8.10 released, my Broadcom card worked out of the box (although, I was using the default GNOME instead of KDE).

Is there anyway to get my wireless card recognized by the KDE Network Manager? 

```
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```

---

### Post by N4zgu1 on 2009-02-19
that happens to me too, i have the same wireless card, and its working fine in linux mint but when i boot slax from my usb it doesnt work

---

### Post by XtremeGamer99 on 2009-02-19
I just booted into my other partition.

This partition originally had Ubuntu 8.10 install, then I upgraded it from 8.10 -> 9.04, and install KDE4. I can boot into either GNOME or KDE, and my wireless works. I'm guessing because it retained the Broadcom driver from 8.10

Then I did a fresh install of Kubuntu 9.04 on another partition to get a clean slate. Did NOT install GNOME. I apparently do not have a driver for my wireless.

In my 8.10 -> 9.04 Ubuntu partition, if I go to "Hardware Drivers" in the menu, it shows "Broadcom STA Wireless Driver" activated and currently in use. If I go to "Hardware Drivers" in my fresh 9.04 Kubuntu install, nothing shows up (something like 'this system is not using any proprietary drivers').

How can I get the driver in my fresh 9.04 install?

---

### Post by krazyd on 2009-02-19
run```
sudo apt-get install b43-fwcutter
```this will download the firmware for your device and get you up and running.

---

### Post by XtremeGamer99 on 2009-02-20
> **krazyd said:**
> run```
sudo apt-get install b43-fwcutter
```this will download the firmware for your device and get you up and running.

Nope. Already tried it, still didn't work.

That's okay though, I figured it out. I had to install linux-restricted-modules (or something to that effect...). Was able to connect wirelessly upon reboot. =)

---

### Post by raakken on 2009-04-05
If you've found a solution to the problem, please post it here, so that others can benefit from your work... 
thanks

---

