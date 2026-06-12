---
title: "Booting from BIOS"
date: 2013-12-30
forum: Installation &amp; Upgrades
---

### Post by gallerianmarlon on 2013-12-30
hello everyone, i hope you are all doing fine! everything has worked for me up until so far,where i am trying to boot Ubuntu from my bootable flash drive. there's a big problem however - my BIOS requires you to use the down arrow key to select "booting from USB" but my down arrow key doesn't work at all. i've tried using the up arrow key to see if that would take me to the bottom of the boot menu, but it doesn't work. i've considered a usb keyboard but i am not sure it would work. i've heard something about "Legacy USB" but i'm not sure if that is going to help with my issue of the keyboard? may i have some advice? thank you!

---

### Post by oldfred on 2013-12-30
My BIOS has settings for USB ports to enable keyboard & mouse.

Both Windows & Ubuntu seem to have drivers and would work, but grub relies on BIOS as it has no drivers. I first found old ps/2 ports worked, but that was huge hassle. Then I found BIOS settings.

And then I found every BIOS update reset back to defaults and I had to enable them again.

---

### Post by gallerianmarlon on 2013-12-30
> **oldfred said:**
> My BIOS has settings for USB ports to enable keyboard & mouse.

Both Windows & Ubuntu seem to have drivers and would work, but grub relies on BIOS as it has no drivers. I first found old ps/2 ports worked, but that was huge hassle. Then I found BIOS settings.

And then I found every BIOS update reset back to defaults and I had to enable them again.

alright this is a pic of my boot menu:
[ATTACH=CONFIG]249029[/ATTACH]
i have minimal settings there as you can see; i press f12 to get into the boot menu but on startup, it shows that you may press f2 to get into setup. i'm wondering how useful that would be? i'm going to check it to see if i have any similar options to yours

---

### Post by gallerianmarlon on 2013-12-30
in setup i found these options (one says wireless?)
[ATTACH=CONFIG]249032[/ATTACH]
though i can't exit setup without saving changes and i'm scared that might do something to my computer's regular booting?

---

### Post by oldfred on 2013-12-30
Escape lets you exit without saving changes. If you have not changed anything, then saving changes will not actually change anything. But if you click restore defaults it changes everything back to defaults.

Not sure what wireless settings you have but the > says you have to click on it as it has more settings under/inside it.

---

### Post by gallerianmarlon on 2013-12-30
so even though it asks me to save configuration changes i guess it does that by default? as soon as i exit setup i'm going to try to put in my usb keyboard and post the results as the setup said something about usb emulation enabled so i'm thinking it will let me use one, but i'm still not positive it will. also, what is usb wake support?

---

### Post by oldfred on 2013-12-30
Some systems can be configured to have power on via Ethernet or USB ports to start up a system. So motherboard is asleep but still checking status of USB port and if signal or power given it then boots. 
Similar to or used by your backup power supply to control startup & shutdown.

---

### Post by gallerianmarlon on 2013-12-30
ah well, i guess i'm gonna have to venture into the depths of my keyboard circuitry. i would use legacy (i found out what it was) to use a usb keyboard but i can't even enable it without using a PS/2 keyboard or the computer's actual keyboard since my down arrow key doesnt function unless it's possible to do things in the BIOS with a mouse. thank you for all the help you provided me though!

---

