---
title: "I can run off Live Cd using nomodeset, but get blank screen if I boot by HDD"
date: 2011-11-27
forum: Installation &amp; Upgrades
---

### Post by Ayveoh on 2011-11-27
Specs:
Dell Dimension E520
Original OS : Windows Vista
Graphics Card: MSI GeForce 9500GT 512MB DDR2 PCI Express
Processor: Q67000
Network card: Airlink Awlh6070

I did a clean install of 10.04 doing a full partition of the drive, and after it installed and asked to reboot, the computer would reboot but then blink " | " and then the monitor would not receive signal from the graphics card.

however if I put the cd back in, and run "try ubuntu without installing" and use nomodeset, I can get it to the desktop.

From there I tried install the Nvidia graphics card, but when I reboot after installing it goes back to blinking.

Help thanks!

---

### Post by cbowman57 on 2011-11-27
When you get to the grub screen select the installation you're trying to boot from & press the **e** key. At the end of the kernel boot line add nomodeset. If it boots then you can install a driver.

---

### Post by Ayveoh on 2011-11-27
> **cbowman57 said:**
> When you get to the grub screen select the installation you're trying to boot from & press the **e** key. At the end of the kernel boot line add nomodeset. If it boots then you can install a driver.

I can't get to the grub screen unless the installation cd is in, and if it is, I can't press e i can only edit using f6...and even then it does not boot.

I can only boot from cd with "try ubuntu" and if i install driver there, it doesn't stick when i boot from HDD

---

### Post by MAFoElffen on 2011-11-27
> **cbowman57 said:**
> When you get to the grub screen select the installation you're trying to boot from & press the **e** key. At the end of the kernel boot line add nomodeset. If it boots then you can install a driver.
+1 Plus... When you're booted into the GUI, go to System settings. Look in the hardware section and start Additional Drivers. Look for the driver that says "Recommended." It will most likely be nvidia-current.

Or you could just install in a terminal via
```

sudo apt-get install nvidia-current

```

---

### Post by cbowman57 on 2011-11-27
> **Ayveoh said:**
> I can't get to the grub screen unless the installation cd is in, and if it is, I can't press e i can only edit using f6...and even then it does not boot.

I can only boot from cd with "try ubuntu" and if i install driver there, it doesn't stick when i boot from HDD

Ok, you're not being presented with the grub menu.

Hold the shift key down when it starts booting up, that should expose it for you.

---

### Post by Ayveoh on 2011-11-27
> **MAFoElffen said:**
> +1 Plus... When you're booted into the GUI, go to System settings. Look in the hardware section and start Additional Drivers. Look for the driver that says "Recommended." It will most likely be nvidia-current.

Or you could just install in a terminal via
```

sudo apt-get install nvidia-current

```

I can only get to GUI using "Try Ubuntu without installing".
Also, It doesn't let me download Nvidia-current it gives me an error, so I have to get another driver.
Once i restart without the disc...i get blank screen.

---

### Post by Ayveoh on 2011-11-27
> **cbowman57 said:**
> Ok, you're not being presented with the grub menu.

Hold the shift key down when it starts booting up, that should expose it for you.

Alright I got to the grub menu by holding shift, and added nomodeset, but then it gives me blank screen again

---

### Post by cbowman57 on 2011-11-27
> **Ayveoh said:**
> Alright I got to the grub menu by holding shift, and added nomodeset, but then it gives me blank screen again

Something sounds screwed up for sure.

Ok, when you get to that black screen try getting to another tty terminal by pressing ctl+alt+f1.  It sounds like the installation didn't install a driver, or screwed up the installation.  If the ctl+alt+f1 (or f2, f3) gets you to a terminal you can login & try what a previous post suggested, sudo apt-get install nvidia-current.

---

### Post by drillerccg on 2011-11-27
I have a related problem: I can bring the installation up by using nomodeset at grub and using e. I also made it permanent by editing grub. My problem is that the screen is using low resolution to my Windows boot on the same computer. Using Intel G43/45 graphic card. Any ides to get better resolution and effects? TIA

for original poster I used this thread:

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Ayveoh on 2011-11-28
> **cbowman57 said:**
> Something sounds screwed up for sure.

Ok, when you get to that black screen try getting to another tty terminal by pressing ctl+alt+f1.  It sounds like the installation didn't install a driver, or screwed up the installation.  If the ctl+alt+f1 (or f2, f3) gets you to a terminal you can login & try what a previous post suggested, sudo apt-get install nvidia-current.

I did another clean install and after running with nomodeset after the GRUB menu, it stalls at a black screen with " _ " in the top left hand corner.

---

### Post by cbowman57 on 2011-11-28
Did you try an alternate tty terminal when it stalled at that screen?

---

### Post by Ayveoh on 2011-11-28
> **cbowman57 said:**
> Did you try an alternate tty terminal when it stalled at that screen?

yeah, it continued to stall there.

---

### Post by cbowman57 on 2011-11-28
Try choosing the recovery option & see if it gets any farther, even if it's just to netroot.

---

