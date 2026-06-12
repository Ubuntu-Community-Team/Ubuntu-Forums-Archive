---
title: "Install: Blank screen at start of install - need way to enable display during install"
date: 2012-01-25
forum: Installation &amp; Upgrades
---

### Post by Redflea on 2012-01-25
Hi - Linux noob here. 

I've been playing w/Ubuntu in a VM for building Android, and have decided I need to give Ubuntu a "real" environment to get better performance.  

I'm trying to install Ubuntu for dual boot on a Sony laptop...I downloaded 10.04.3 ISO and burned a CD with it, have verified on another computer the CD works, everything displays properly. 

On the Sony Viao laptop, (VPC CW290L, Nvidia Geforce 310M/320M/330M series graphics, Win 7 Pro), Every time I start install, or even try to run the demo version from the CD, or anything requiring Ubuntu to display anything other than language selection and the initial menu in Demo mode, the screen goes blank...I can hear things running in the background, but no display.  

So I'm blocked from installing.  

I've been told that I can set some command line parameters to start an install with graphics display working, and presumably once I'm installed I can also enable the display...

When I boot from the CD I never see any GUI, but if I press space bar when the prompt comes up I can see the Advanced page, so I believe that does give me access to changing the graphics parameter so the GUI will work...just need to know what to do. 

Would really appreciate some advice/help with this.

And if this means that trying to run Ubuntu on this laptop is a bad idea, please let me know.  :)

More info:  The laptop's resolution appears to be 1366 x 768. 

I started playing w/the VGA= parameter...Help (which luckily shows up in text mode on-screen) says to use vga-771 for "Laptops with display problems" and that did not work, same blank display as soon as the install starts and tries to go to GUI.   

When I put in 824 (vesa mode 1024x768, from the "Linux Video Mode Numbers" table [http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers)), I got a message that the setting was not supported (strangely the message says "Undefined video mode number 338" - no mention of 824) and I was offered a text list of resolution options by the install, each install has a number 0-9 or letter a-x, etc., next to it.  Tried the option that was 1360x768x32, and that failed...

I've tried a bunch of modes, 1024x768x32 and x16, 1360x768x32 & x16, 800x600x16...not working.  Screen goes blank (as it turns off) as soon as the install starts after selecting video mode.

Help!  :)

---

### Post by Quackers on 2012-01-25
Try the nomodeset boot option

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Redflea on 2012-01-25
> **Quackers said:**
> Try the nomodeset boot option

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Excellent!  Installing now, thanks very much for pointing me to that thread...I should have found it on my own, my ninja search skills were clearly lacking last night!  :)

---

### Post by Quackers on 2012-01-25
> **Redflea said:**
> Excellent!  Installing now, thanks very much for pointing me to that thread...I should have found it on my own, my ninja search skills were clearly lacking last night!  :)

No problem, I'm sure it's just the time of year for Ninja skills to be dulled ;)

---

