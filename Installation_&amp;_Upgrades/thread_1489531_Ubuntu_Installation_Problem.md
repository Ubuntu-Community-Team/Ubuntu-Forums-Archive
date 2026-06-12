---
title: "Ubuntu Installation Problem"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by udaka on 2010-05-21
Hi

I have burned the .iso file on a cd and tried to install it on my old laptop. I want to install only Ubuntu, without any Windows version.

Once the installation start with the Ubuntu screen, after fews minutes the screen goes like in stand by mode, it turns black and the only command the pc respond to is the shooting down, some fast dos writes show up on the screen and suddenly the ubuntu screen says "remove cd and press any key", I do it, the laptop shoot down, and when I restart it there is nothing inside.

My knowledge are not so big in hardware, bios and so on, so I attache a report of my laptop hardware configuration, I hope with this informations someone could help me. 

Many thanks in advance ;)

---

### Post by CSInDevelopment on 2010-05-21
Sounds like the disc didnt burn / download right.
Try with another disc, if it still doesnt work then try another distro just to be sure it isnt the system.
sorry if this wasnt helpfull...but I havent had any trouble that early in use of it unless the hardware was dodgy or the disc wasnt compatible...such as 64-bit running on a 32-bit only cpu

---

### Post by udaka on 2010-05-21
I have already burned 2 discs and at 8x speed, just to eliminate any risk of error. What do you refers to with "distro"??

Have you had a look to my laptop attached report? I cant understand so far if the hardware is not compatible...thanks a lot for helping

---

### Post by darkod on 2010-05-21
Have you tried to run it first in live mode? If it doesn't load live mode correctly, it probably won't run correctly after install or with not be able to install at all. Not without additional instructions/commands.

---

### Post by udaka on 2010-05-21
Hi Darko

What you mean with "live mode", sorry I am not so expert..

---

### Post by darkod on 2010-05-21
> **udaka said:**
> Hi Darko

What you mean with "live mode", sorry I am not so expert..

Ubuntu has the option to run from the cd first without making any changes to your computer. Usually called live mode, or liveCD. It is a fully working system but running from the cd.

If there are any hardware issues, live mode will show them (it won't run OK). If it runs OK, you can expect ubuntu to work fine after installing it too.

When you boot with the ubuntu cd, select Try Ubuntu for live mode, don't start the install process.

---

### Post by udaka on 2010-05-21
For what I can see on the screen even the option descrived by you, the live mode, is it not available on my laptop. It just starts with a low resolution Ubuntu screen and starts some procedure...but it not gives to me the option to choose.
I have downloaded the Ubuntu.iso file from the Ubuntu web and burned that image with Nero on a cd, twice, I don't know if there could be something wrong.

---

### Post by sir-jasper on 2010-05-21
I have the same on a Latitude 505 again with 10.04.  From the initial option screen to Try or install either option starts to read the CD and then goes into a sort of standby mode where the screen is still on but black, no activity on CD or hard drive and sits there (at lease 15 minutes).  CD is OK as I'm currently installing it from within windows.  I did install version 9 on a Latitude last year.

---

### Post by darkod on 2010-05-21
OK, lets try this. When the ubuntu cd starts booting, hit any key when the ubuntu image is shown.

That should show you a boot menu with Try Ubuntu, Install Ubuntu, Memtest, etc. At the bottom on the screen there are additional options. Hit F6 for advanced options and select Safe Graphics. After that Try Ubuntu from the main menu.

When you say the live mode option is not available, you mean it doesn't load correctly, or there is nowhere to select Try Ubuntu?

---

### Post by sir-jasper on 2010-05-21
Tried selecting noapic and nolapic and then adding vga=771 (as suggested in the help screen).  Try or install have the Ubuntu logo with the dots underneath going white to red.  I suspect the screen then tries to go to something else at which point mine goes blank and then after about 15 seconds CD and hard drive cut out and it just sits there.

Does this give any additional pointers?

---

### Post by darkod on 2010-05-21
> **sir-jasper said:**
> Tried selecting noapic and nolapic and then adding vga=771 (as suggested in the help screen).  Try or install have the Ubuntu logo with the dots underneath going white to red.  I suspect the screen then tries to go to something else at which point mine goes blank and then after about 15 seconds CD and hard drive cut out and it just sits there.

Does this give any additional pointers?

Not to me, sorry.

I have also read people needing to add nomodeset at the end of the command line for booting ubuntu, but right now from the top of my head I can't explain how to get the boot command to show. Maybe the F6 can help, or highlighting the Try Ubuntu entry but hitting 'e', not Enter. That should show you boot lines for edit. Use the arrows keys and End to go to the end of the line starting with 'linux' and add nomodeset at the end. Hit Ctrl + X to try to boot.

---

