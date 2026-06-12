---
title: "Problems booting Ubuntu on my new desktop!"
date: 2011-03-19
forum: Installation &amp; Upgrades
---

### Post by effay on 2011-03-19
Hi all!

In January I built a new desktop with the following specs:
-CPU: AMD Athlon II X3 445
-Motherboard: Gigabyte GA-770T-USB3
-Memory: ADATA DDR3-1333 SDRAM AD3U1333B2G9-DRH (4 x 2GB)
-Graphics card: Palit GeForce GT 240 (512 MB GDDR5)
-Internal HD: Western Digital Caviar Blue WD5000AAKS 500GB
-External HD: Seagate Expansion External Drive ST310005EXA101-RK 1TB
-Optical drive: LiteOn iHBS112 Blu-ray/DVD/CD writer
-Optical drive: LiteOn iHES208 Blu-ray reader & DVD/CD writer
-Wireless adapter: EnGenius EUB-9801
-PSU: Corsair Enthusiast Series TX650W
-Monitor: Asus VH222H (21.5" LCD)

So I have W7U installed on my internal HD and I want to have 10.10 on my Seagate external HD. I connected the Seagate to my old laptop (Toshiba Satellite A130-ST1312) and installed 10.10 and the bootloader on the Seagate. Ubuntu works fine when I boot the Seagate while connected to my laptop, so all is well so far.

The problem is when I try to boot the Seagate from my desktop I get the GRUB screen that asks me to choose which OS to boot, I choose Ubuntu, and then the screen goes mostly black except for a random spattering of randomly colored pixels and freezes like that. I have no idea what to do and I've been scouring forums for my hardware and trying all kinds of random stuff.

Also, the reason I had to install Ubuntu from my laptop is because a similar problem arises when I try to boot the 10.10 ISO CD on my desktop. The waiting screen with Ubuntu on top of the 5 or so dots appears and then transitions to a weird, messed-up, blocky collage of the Windows 7 desktop and freezes that way.

Since 10.10 messes up in a similar way when I try to boot the Seagate or when I try to boot the ISO CD, I'm led to suspect some sort of incompatibility with my CPU, motherboard, or graphics card. Unfortunately, I haven't been able to determine what to do.

Any thoughts!?

---

### Post by Quackers on 2011-03-19
That looks like a graphics problem on your desktop. What graphics card are you using? You may need a boot otion, like nomodeset, for instance.

---

### Post by effay on 2011-03-19
Thanks for the quick reply Quackers!

I have a Palit GeForce GT 240 with 512MB GDDR5.

Could you elaborate on what a boot option and nomodeset are and how this might fix things? I'm not familiar with graphics boot stuff...

---

### Post by Quackers on 2011-03-19
On your desktop at the grub menu screen, make sure that Ubuntu is highlighted (usually the top option) and press the "e" key, to edit. A new screen will appear. Using your down arrow and "end" key navigate to the end of the line which currently ends with "quiet splash".
With the backspace key, delete those two words then type in "nomodeset" - without the quotes.
Then press ctrl+X to boot.
See if the system then boots. If it does, install any additional drivers through System > Admin > Additional drivers. If graphics drivers are available install them and reboot. 
Your system may now boot without using that boot option.
If no drivers show as being available, it may be that you will have to use the nomodeset option permanently. To do that you can read details here
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by effay on 2011-03-20
Your method worked flawlessly! Thanks!!

---

### Post by Quackers on 2011-03-20
I'm glad it did :-)
If you have installed graphics drivers you won't need to use the boot option again - probably :-)

---

