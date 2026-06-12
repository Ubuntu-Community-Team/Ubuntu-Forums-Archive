---
title: "PS/2 mouse is not working (ubuntu 9.04)"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by nlshant on 2010-02-19
[SIZE=2][COLOR=black]Hi All, [/COLOR][/SIZE]
 
[LEFT][SIZE=2][COLOR=black]PS/2 mouse is not working on my newly installed Ubuntu[/COLOR][/SIZE][/LEFT]
 
[LEFT][SIZE=2][COLOR=black](ver:9.04). Please help me to solve [/COLOR][/SIZE][SIZE=2][COLOR=black]issue. [/COLOR][/SIZE][/LEFT]

---

### Post by djchandler on 2010-02-19
> **nlshant said:**
> [SIZE=2][COLOR=black]Hi All, [/COLOR][/SIZE]
 
[LEFT][SIZE=2][COLOR=black]PS/2 mouse is not working on my newly installed Ubuntu[/COLOR][/SIZE][/LEFT]
 
[LEFT][SIZE=2][COLOR=black](ver:9.04). Please help me to solve [/COLOR][/SIZE][SIZE=2][COLOR=black]issue. [/COLOR][/SIZE][/LEFT]


Did it work when running the Live CD?

We need more information in order to help you. What is actually occurring and when?

---

### Post by nlshant on 2010-02-19
> **djchandler said:**
> Did it work when running the Live CD?
 
We need more information in order to help you. What is actually occurring and when?
 
HI,
 
I didnt check with Ubuntu LIVE CD.  On windows XP and Feora Core 9 the mouse is 
 
working. Also I checked with Ubuntu 9.10 and is working fine.  While installing im able 
 
to use the mouse but when installation is over and reboots im not able to use.  Ubuntu 
 
is showing the mouse pointer but its not moving :(. 
 
 
If any more information needed please let me know.    
    
 
System Configuration : Acer VERTION (  Intel Core 2 Duo Processor, MSI MS7259 Mother board , One 160GB Sata HDD, One 20GB IDE HDD( Ubuntu is installed On), acer ps/2 Optical mouse, acer keyboard.

---

### Post by djchandler on 2010-02-20
> **nlshant said:**
> While installing im able to use the mouse but when installation is over and reboots im not able to use.  Ubuntu is showing the mouse pointer but its not moving :(. 

 [COLOR=Black]See if the laser light is on in the mouse. If it is not, [COLOR=Black]y[/COLOR]ou may be able to mask the problem by disabling USB legacy device support in your BIOS. If it's currently disabled, try enabling.

There's [/COLOR][COLOR=Black]apparently [/COLOR][COLOR=Black]been a persistent bug in the [/COLOR][COLOR=Black]driver/kernel [/COLOR][COLOR=Black]blob [/COLOR][COLOR=Black]provided for the i8042 PS/2 decoder chip. If that driver is being used (due to mimicry) to interface your PS/2 ports with the [/COLOR][COLOR=#666666][COLOR=Black]VIA P4M800 chipset, that could be the problem.

My guess is that your system is looking for the mouse on the USB port. Toggling the USB BIOS setting forces the hardware configuration to be re-read and then appropriate config files created.
[/COLOR]
[/COLOR]

---

### Post by nlshant on 2010-02-24
**Hi **djchandler**, **
 
 
**      Thank you for the resolution. I will try disabling USB Legacy support and **
 
**let you know. **
 
**Regards, **
**Nishant. **
 
 
> **djchandler said:**
> [COLOR=black]See if the laser light is on in the mouse. If it is not, [COLOR=black]y[/COLOR]ou may be able to mask the problem by disabling USB legacy device support in your BIOS. If it's currently disabled, try enabling.
 
There's [/COLOR][COLOR=black]apparently [/COLOR][COLOR=black]been a persistent bug in the [/COLOR][COLOR=black]driver/kernel [/COLOR][COLOR=black]blob [/COLOR][COLOR=black]provided for the i8042 PS/2 decoder chip. If that driver is being used (due to mimicry) to interface your PS/2 ports with the [/COLOR][COLOR=#666666][COLOR=black]VIA P4M800 chipset, that could be the problem.[/COLOR]
 
[COLOR=#666666]My guess is that your system is looking for the mouse on the USB port. Toggling the USB BIOS setting forces the hardware configuration to be re-read and then appropriate config files created.[/COLOR]
 
[/COLOR]

---

