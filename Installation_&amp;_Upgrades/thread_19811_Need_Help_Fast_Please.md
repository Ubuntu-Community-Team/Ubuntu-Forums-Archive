---
title: "Need Help Fast Please"
date: 2005-03-13
forum: Installation &amp; Upgrades
---

### Post by EvilButters on 2005-03-13
I just istalled Ubuntu and when I go to start it up, the XSEVER starts but my montior says Screen Resolution to big, but I can start in safe mode and type in a command to the root so I was wondering what do I type in to fix this prolbem?

Version: Warty Warthog
Montior:  HP Pavilion f1703
Video Card: ATI

Thanks For The Help in advance

---

### Post by Insanely on 2005-03-13
ummm.

There are two ways we can try and fix this:

1. Try xf86config (can't remember if warty uses this. Hoary 5.04 uses xorgconfig)
 and it will ask you a series of questions. These questions will be specific to your hardware.

OR

2.
goto /etc/X11
sudo cp XF86Config-4 XF86Config-4.backup
sudo pico XF86Config-4

I am not in front on a linux box atm so I will have a guess. If you scroll down to a section called monitor you should have a list of screen resolutions to use with certain color profiles. IE:

"1280x1024" "1024x768" etc...

I would remove any resolutions that your monitor can't handle. Or simple just add these resolutions in:
"1024x768" "800x600"

If you now your monitors hsync and vrefresh add them in. Otherwise leave it alone. Save the file with control + x and hit "y" to save.

I'm not entirely sure this will work. I am not the most confident user with linux but I had a similar issue before and the second step worked.

---

### Post by az on 2005-03-13
"OR

2.
goto /etc/X11
sudo cp XF86Config-4 XF86Config-4.backup
sudo pico XF86Config-4

I am not in front on a linux box atm so I will have a guess. If you scroll down to a section called monitor you should have a list of screen resolutions to use with certain color profiles. IE:

"1280x1024" "1024x768" etc...

I would remove any resolutions that your monitor can't handle. Or simple just add these resolutions in:
"1024x768" "800x600"

If you now your monitors hsync and vrefresh add them in. Otherwise leave it alone. Save the file with control + x and hit "y" to save."


If you ever update that package, the information will be overwritten the next time.  You must change the setting in debconf or never ever update your system.

The way to go is:
dpkg-reconfigure xserver-xfree86
and when asked about monitor setting pick medium and play around with the choices you are offered.  Maybe your card does not have enough memory for high color depths.  Try a color depth of 15 bits....

---

