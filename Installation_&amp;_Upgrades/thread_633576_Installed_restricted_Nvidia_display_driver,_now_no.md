---
title: "Installed restricted Nvidia display driver, now no display on monitor."
date: 2007-12-06
forum: Installation &amp; Upgrades
---

### Post by tmcarson1 on 2007-12-06
I enabled the restricted display driver for my Nvidia card, and after reboot I have no display on my screen, I can hear Ubuntu starting up, but my monitors lights (standby and on) are both on.

How can I disable this driver to get back into ubuntu or is this even possible?

Thanks

---

### Post by Pumalite on 2007-12-06
Cofigure your xserver. Once IN the system, you can fix things.
Ctrl+Alt+F1 to get command line
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
Accept most defaulrs, choose 'vesa' as the driver
Then: startx
Or sudo /etc/init.d/gdm start
Go to your cards site and figure out what driver you need or can use.
Come back if you need more help.

---

### Post by tmcarson1 on 2007-12-06
Thanks, will give it a try right now.  Will post the results.

---

### Post by tmcarson1 on 2007-12-06
Thank you, it worked fine and I am now back in ubuntu.

It did tell me this though at the end:

xserver-xorg postinst warning:
overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.20071206183742

Is this just advisory and nothing to be concerned with?

Also, since after enabling the restricted Nvidia driver and getting undesirable results, does this mean I cannot use the nvidia driver at all with ubuntu?

Thanks so much for your help!

---

### Post by jdt141 on 2007-12-06
Why do you want to use the nvidia driver? If it ain't broke...

---

### Post by Pumalite on 2007-12-06
If you followed my advice, you should have now 'vesa' as the driver. You can check the /etc/X11/xorg.conf file. The restricted driver does not work with your video display. You can check your motherboard (not possible if it is a laptop) and check ig you have an AGP slot. In that case you could install an Nvidia 6600 GS AGP or similar and have your restricted driver working.

---

### Post by tmcarson1 on 2007-12-07
Thank you for all your help!

---

### Post by Pumalite on 2007-12-07
You are welcome. Good luck.

---

