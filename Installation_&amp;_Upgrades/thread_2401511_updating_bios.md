---
title: "updating bios"
date: 2018-09-19
forum: Installation &amp; Upgrades
---

### Post by pretzel85 on 2018-09-19
Hi guys,

I'm new to Ubuntu and I already need the help of the community. :)

Problem: After putting my notebook into hibernation mode by closing its lid, it won't wake up again. The power button and some other leds will be blinking, but there won't be any reaction when pressing any keys or buttons, which ultimately requires a restart.
What I've already tried: 
- I've downloaded the latest bios bootable iso file ([https://download.lenovo.com/eol/;](https://download.lenovo.com/eol/;) BIOS Update bootable CD), 
- converted it into an image file with geteltorito and shifted the so created file on my usb stick.
- I've restarted my notebook and pressed F12 to change the booting device to USB, which ultimately leads to the following message: Missing operating system.

ubuntu: 18.04
notebook: lenovo thinkpad w510

I'd really appreciate any help, since this problem is a bit of a nuisance.

Cheers,
pretzel

---

### Post by ajgreeny on 2018-09-19
If the power button and other LEDs are still active (blinking) the machine must be in suspend mode not hibernation which is disabled by default in Ubuntu.

Have you actually set Hibernate as the action to be taken when closing the lid? If so, change that to Suspend and see if it makes any difference; I am not sure it will , but let's look at the easy things first before trying others.

---

### Post by westie457 on 2018-09-19
Over on the Lenovo Forums the suggestion for a Thinkpad and some other machines is to disconnect the battery and the power cable, hold the power button down for 10 seconds, reconnect the battery and power on.

---

### Post by pretzel85 on 2018-09-19
You are right. I was actually talking about suspend mode, not about hibernation. I haven't configured anything regarding the power management so far. I just want my notebook to wake up again when opening the lid.

---

### Post by westie457 on 2018-09-20
If your computer put itself to sleep because the power cable was left in without the screen using power see my previous post.

---

