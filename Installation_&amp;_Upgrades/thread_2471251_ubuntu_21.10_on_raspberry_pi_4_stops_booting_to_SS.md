---
title: "ubuntu 21.10 on raspberry pi 4 stops booting to SSD after routine software update"
date: 2022-01-24
forum: Installation &amp; Upgrades
---

### Post by tcab on 2022-01-24
My ubuntu 21.10 on raspberry pi 4 running off SSD was running happily for several months.  

However after saying YES to a routine software update (prompted for on the desktop) it said it needed to reboot. So I say OK.  

Now Ubuntu stops booting to SSD - Bios/text boot message says its searching for the SD Card in an infinite loop - I don't have a SD card present since as I say, I've been booting and running happily off SSD.  
Is this known about/fixable?

---

### Post by tcab on 2022-01-25
[COLOR=#555555]I managed to fix the situation.

[/COLOR]The clue was in ejolson's comment in [this post]("https://forums.raspberrypi.com/viewtopic.php?t=293662") which said:
> [COLOR=#555555][FONT=Roboto]I suspect the new update erased the boot order option and you need to reenable the USB boot in the firmware.

[FONT=Verdana]So I followed the first half of [/FONT][this tutorial]("https://www.tomshardware.com/how-to/boot-raspberry-pi-4-usb")[FONT=Verdana] regarding updating the firmware on the Pi to (re-)enable boot from SSD. Basically
- Use Raspberry Pi Imager and select the operating system to burn to a fresh SD Card to be "[/FONT]Misc Utility Images"/"Bootloader"/"USB Boot"
[FONT=Verdana]- Boot the Pi from that SD Card - after 10 seconds the screen will turn green and the update process is complete
- Power off the Pi, take out the SD Card, plug in your Ubuntu SSD again, and power on.

The Pi should now correctly boot from SSD again and Ubuntu springs back to life.

[/FONT]
[/FONT][/COLOR]

---

