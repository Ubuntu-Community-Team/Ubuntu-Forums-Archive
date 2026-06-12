---
title: "ath5k driver"
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by thor2002ro on 2008-10-14
hi the kernel update from today killed  Atheros driver ath5k

the board is  Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

in my acer aspire one 150

```
[  725.402671] ath5k_pci 0000:03:00.0: PCI INT A disabled
[  731.747811] ath5k_pci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  731.747875] ath5k_pci 0000:03:00.0: setting latency timer to 64
[  731.750138] ath5k_pci 0000:03:00.0: registered as 'phy0'
[  731.754658] ath5k phy0: Support for RF2425 is under development.
[  731.796499] phy0: Selected rate control algorithm 'pid'
[  731.799257] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[  736.473470] ath5k phy0: gain calibration timeout (2412MHz)
[  736.473488] ath5k phy0: unable to reset hardware: -11
[  737.108607] ath5k phy0: gain calibration timeout (2412MHz)
[  737.108624] ath5k phy0: unable to reset hardware: -11

```

---

### Post by sigmabetatooth on 2008-10-14
Dito on that killed ath5k driver.  Please let me know what helpful outputs from my Compaq Presario C700 I should post.

Here's a little to start with...
> sww@oy:~$ dmesg | grep ath5k
[   28.644942] ath5k_pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   28.644978] ath5k_pci 0000:01:00.0: setting latency timer to 64
[   28.645044] ath5k_pci 0000:01:00.0: registered as 'phy0'
[   28.649448] ath5k phy0: Support for RF2425 is under development.
[   28.920158] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   33.295456] ath5k phy0: gain calibration timeout (2412MHz)
[   33.295465] ath5k phy0: unable to reset hardware: -11
[   33.654897] ath5k phy0: gain calibration timeout (2412MHz)
[   33.654906] ath5k phy0: unable to reset hardware: -11
[  183.519460] ath5k phy0: gain calibration timeout (2412MHz)
[  183.519470] ath5k phy0: unable to reset hardware: -11
[  953.105870] ath5k phy0: gain calibration timeout (2412MHz)
[  953.105879] ath5k phy0: unable to reset hardware: -11


---

### Post by thor2002ro on 2008-10-15
weird when i started the laptop this morning now it works....and i didnt do nothing :|

---

### Post by inportb on 2008-10-15
> **thor2002ro said:**
> ...and i didnt do nothing

You rebooted. Or at least power-cycled. :)

---

### Post by thor2002ro on 2008-10-15
> **inportb said:**
> You rebooted. Or at least power-cycled. :)

it was cloased for the night i think the shutdown was necesary for the card to reset ... , restarts i tried last night , tryed removiing the ath5k module and reloading it nothing worked lol. some times the answer is so simple ^^

now : the changes i see is that the new kenrnel loads new ath5k and now it loads in led module . the lead still doesnt work but i think they are working on it :D

---

### Post by endotoxin on 2008-10-15
I too am running an ath5k driver, until I received the header updates this evening. I surfed around and followed the instructions at [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download) , but was unable to get them to launch. Of course, I just tried 'sudo modprobe ath5k' and immediately recovered wireless support.

That'll teach ME not to keep a backup copy of the drivers for download!

---

### Post by thor2002ro on 2008-10-16
the update is good just shut down computer compleatly and reopen it worked great ... as far as i can tell the board get stck somehow and the driver cant recover it .... but a compleate shut down fixes it

---

### Post by baizon on 2008-10-16
Hi, i've had the same problem. Anfer a Kernel-Upgrade i was getting the same errormsg. My solution was to disable the Wifi Card (in the BIOS) and enable it again, then it worked again.

---

### Post by Bavo on 2008-10-16
> **baizon said:**
> Hi, i've had the same problem. Anfer a Kernel-Upgrade i was getting the same errormsg. My solution was to disable the Wifi Card (in the BIOS) and enable it again, then it worked again.

I have the same problem
I didn't have to disable the device, just a cold boot did the trick.

I tried a few reboots but that just doesn't do the trick, you have to shut down your computer entirely and then boot again.

---

### Post by jfernyhough on 2008-10-16
Another useful tip for laptops when things don't work that used to is to power down, remove the battery, wait, reinsert the battery, and power up again. It's the ultimate cold boot (well - apart from removing the CMOS battery too...).

---

### Post by taavikko on 2008-10-16
I haven't had any problems using ath5k in my aspire-one notebook.
It works only annoyance is slow speeds, NM states it 5-12Mb, as it should be 54Mb. 
But it's still under devel, so I would suspect that time will fix this :)

---

### Post by tensop on 2008-10-16
donate some money to madwifi and things will move along quicker ;D

---

### Post by taavikko on 2008-10-16
> **tensop said:**
> donate some money to madwifi and things will move along quicker ;D

already contributing to several projects, by giving them money.
Far more satisfying than to buy windows license ;)

---

