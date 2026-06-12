---
title: "PAE in 11.04"
date: 2012-03-19
forum: Installation &amp; Upgrades
---

### Post by schopen on 2012-03-19
Welcome.
I have just replace my single SODIMM 2 GB RAM with 2 x 4 GB RAM, that's why i want use PAE in Ubuntu.
I am having installed initrd.img-2.6.35-32-generic and i tryied install initrd.img-2.6.35-32-generic-pae kernel, but it doesn't work.
When i try run PAE kernel Ubuntu is loaded but without graphical environment.
In console mode i could run top and htop to check if 8 GB RAM has been detected and everything is ok.
I have Radeon HD 4250. I am not sure - perhaps something with graphical drivers is wrong?
If someone had similar experience please help me :)

---

### Post by ajgreeny on 2012-03-19
> **schopen said:**
> Welcome.
I have just replace my single SODIMM 2 GB RAM with 2 x 4 GB RAM, that's why i want use PAE in Ubuntu.
I am having installed initrd.img-2.6.35-32-generic and i tryied install initrd.img-2.6.35-32-generic-pae kernel, but it doesn't work.
When i try run PAE kernel Ubuntu is loaded but without graphical environment.
In console mode i could run top and htop to check if 8 GB RAM has been detected and everything is ok.
I have Radeon HD 4250. I am not sure - perhaps something with graphical drivers is wrong?
If someone had similar experience please help me :)
The command ```
free -m
``` will tell you how much ram is recognised.

As for lack of gui, perhaps you just need to reinstall the driver again, now that the new kernel has been installed.  I'm not totally sure how you do that from a command line as I don't know the package name, but you should be able to find what you have installed at the moment from synaptic.

---

### Post by sudodus on 2012-03-19
Here are some suggestions what to try:

Do you remember what graphical driver (for the Radeon card) you were using before? Can you find the interface for trying the drivers that are offered by the internal system (proprietary drivers)? If not, maybe you can tell us more about your computer, for example the version and flavour of Ubuntu (is it 'vanilla' Ubuntu 11.10 or something else).

How does it work, if you run a live session 'testing' from the Ubuntu install CD or USB drive? Then, after running a while, you should get an offer to install proprietary drivers. That's the interface I'm talking about.

If that driver does not help, the next step would be to download a proprietary driver directly from the manufacturer, but that is harder, and I suggest that you browse the Ubuntu Forums for threads about it before trying.

---

### Post by schopen on 2012-03-21
Thanks for answer.
I found addictional drivers in System -> Administration.
Removing graphics drivers helped and Ubuntu with PAE Kernel work properly but what i lost after removing it is changing brightness by 1 using function keys.
I do research and i have 0..9 brightness level but after single pressing function key it change by 3.
How to set it to be able changing brightness level by 1 using Function keys?

---

### Post by sudodus on 2012-03-21
I can't help you with that, because I have another brand of graphics (nvidia) and the drivers for that card.

Maybe you can try to add a proprietary driver to your new kernel, and then you will have a better functionality of the graphics. But if the quality of video playing is good, I suggest you keep it, even if it means that some of the setting methods are a bit crude.

---

### Post by schopen on 2012-03-21
I am able to set brightness level between multiples of three typing:
echo 2 > /sys/class/backlight/acpi_video0/brightness
but it's not comfortable.

---

### Post by sudodus on 2012-03-21
It would be a little more convenient to use an alias, try for example
```
alias brt='echo 2 > /sys/class/backlight/acpi_video0/brightness'
```and get the action typing only ```
brt
```or if it should be flexible
```
alias brt='echo > /sys/class/backlight/acpi_video0/brightness'
```and get the action typing for example ```
brt 2
``` or ```
brt 5
```If you enter the alias line into the file ~/.bashrc, it will be available automatically

---

