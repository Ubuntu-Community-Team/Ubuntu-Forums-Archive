---
title: "Installing Ubuntu on Lenovo Yoga Tablet 2 Pro"
date: 2015-01-24
forum: Installation &amp; Upgrades
---

### Post by mrjohnc on 2015-01-24
Hi All

I'm wondering if it's possible to install Ubuntu on the Lenovo Yoga Tablet 2 Pro, please note this is the tablet not the laptop, [here's the page on Lenovo's website for more info]("http://shop.lenovo.com/us/en/tablets/lenovo/yoga-tablet-series/yoga-tablet-2-pro/").

Any help would be appreciated.

Many thanks

John

---

### Post by kerry_s on 2015-01-24
does it have a bios you can boot from usb to install?
if so i would make a usb & try to run it live see what works.

---

### Post by mrjohnc on 2015-01-24
It may do, is there something I would have to do to get it to boot from USB? I'm much more used to fiddling with PC's bios settings

Thanks very much

John

---

### Post by kerry_s on 2015-01-24
lol, you answered my question with a question. what do you see when it boots?
it's android on a x86 cpu, what i'm wondering is if it has a bios that is handing off too start android or if it's like all other androids that has a recovery?

normally when you boot a x86 device with bios, it will show you a screen with what to push to enter bios or boot from other devices. 
if theres no bios you need to hack ubuntu on there from android, there are plenty of how to's on the web for that.

---

### Post by b00n on 2015-03-04
I recently got the 10" version w/ 32 GiB flash and keyboard, which comes running MSWindows:

[http://support.lenovo.com/us/en/products/tablets/yoga-series/yoga-tablet-2-1051](http://support.lenovo.com/us/en/products/tablets/yoga-series/yoga-tablet-2-1051)

I'd like to erase MSWindows and run Ubuntu.

I plugged in a USB keyboard and pressing F2 early/fast enough after power-on takes me to "Novo Menu", listing


[LIST]
[*]Normal startup
[*]BIOS setup
[*]Boot menu
[*]System recovery
[/LIST]
 
The only thing listed under Boot is "Windows Boot Manager".  (It's not really an "option" if there's no other choice!?)

The BIOS (apparently Insyde) has fewer options than anything I have seen before.  I tried

USB Debug support off -> on
Seucre boot on -> off
Exit saving changes

No dice.  I verified the settings had been saved.  The only other options I see are change date/time, "BIOS back flash" on/off, and a couple of reset options.

 In MSWindows under "Options > Update and Recovery > Recovery > Advanced Startup" one of the options is to boot from an alternate device.  I tried that with a USB key plugged in that is a bootable Ubuntu (the standard live install), but it just complained there was no such choice and booted MSWindows.

Do folks have suggestions what else I can try?

---

