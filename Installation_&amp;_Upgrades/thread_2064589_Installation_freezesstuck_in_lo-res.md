---
title: "Installation freezes/stuck in lo-res"
date: 2012-09-29
forum: Installation &amp; Upgrades
---

### Post by MadCityGeoff on 2012-09-29
Hi, everyone. I'm trying to install Ubuntu 12.04 as a dual-boot system on a computer with Win7 installed. My computer is:

Intel Core I7-2600 CPU
Gigabyte Z68XP-UD3 motherboard
Nvidia GTX 580 GPU
Dell S2330MX 23" monitor
128 GB SSD primary drive
1 TB hard drive
Netgear USB wireless networking adapter
USB keyboard/mouse

I burned the Ubuntu 32 bit iso onto a DVD and booted with it. When I got to the screen where you select a language and choose to install or try the OS, the system froze and I had to shut down. On the next boot attempt, I pressed a key to get the screen with the boot options and I selected the option to try without installing. That got me a screen with the Ubuntu logo, then the system locked up again.

After doing some online research, I tried booting with the "nomodeset" option. That let me boot the OS off the DVD, although when I got to the Ubuntu desktop, it was in lo-res and it was surrounded by a black border on the display. I looked at the display settings and the only option is a "laptop" display. Also, there's no networking available. 

I'm about at the end of my technical skills here and I'm not sure how to proceed or if the problem (whatever it is) can be fixed. I'd really appreciate any help you could offer.

---

### Post by Black September on 2012-09-30
This sounds very much like the problem im having on a  Asus Pro 50G series
- CPU: Pentium T3200 2.0GHz
- RAM 2 GB
- HDD: 250 GB
when trying to install Ubuntu 12.04, not dual booting it though.

I have not tried the "nomodeset" option yet tho, will try that now.

---

### Post by Black September on 2012-09-30
Chose the "nomodeset" option and managed to complete the installation.

When it rebooted it just hung at the purple screen with the cursor.

Rebooted again and started in recovery mode (holding down SHIFT during boot), then selected to boot as normal from that menu.

Got to log in and got a popup saying that additional drivers were available. Rebooted again.

This time i came directly to the login screen and managed to log in.

Its currently downloading updates (111 of them...) but so far so good :)

Hope this can help you as well

---

### Post by MadCityGeoff on 2012-09-30
It sounds like you're making good progress so far. Thanks for letting me know. I'll be interested to hear how your system is working after all the downloads are completed. Are you stuck in lo-res mode like I was with the live CD? I suspect that my system might work better with an updated Nvidia driver, although I'm not sure how to get it since my wifi adapter isn't working, at least off the live CD. Oh well... one piece at a time.

---

### Post by 2F4U on 2012-09-30
If you have the chance to get online through a wired connection, Ubuntu would probably suggest appropriate drivers for both your wireless adapter and your graphics card through the restricted drivers application. If there is an appropriate driver for your graphics card, you will most likely get a better resolution.

---

### Post by Black September on 2012-09-30
After the updates, and another reboot, everything works as expected.

Can connect using both wired and wireless, the wired connection worked after i started in recovery mode and 
enabled me installed the nvidia driver.
The graphics are as good as they can get on this laptop now and it looks like the installation is working.

---

