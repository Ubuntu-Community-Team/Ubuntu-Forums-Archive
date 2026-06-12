---
title: "Installation and Graphics Help"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by llloyd on 2008-07-05
Hi! I booted up the Xubuntu live cd and the graphics were *huge*... When I clicked on Install the window went off the edge of the screen. 

So I rebooted, pressed F4, selected a higher resolution, then booted back into the Live cd again and it ignored what I set and was again *huge*... 

In the Settings -> Display only lists "Default" and 320x230 ... How do I set the resolution higher so I can install? Thanks!

L. Lloyd

Oh! It would probably help... This system is a DOS game box (kinda stuck on it for the moment, the main computer is down due to a hardware failure) so it has a Voodoo 3 3000 16mb video card plugged into a 19" WS flat panel monitor. In Win98SE I use 1280x1024 resolution with large fonts and it's not bad. That's what I used when I pressed "F4" at the initial boot screen.

---

### Post by overdrank on 2008-07-05
> **llloyd said:**
> Hi! I booted up the Xubuntu live cd and the graphics were *huge*... When I clicked on Install the window went off the edge of the screen. 

So I rebooted, pressed F4, selected a higher resolution, then booted back into the Live cd again and it ignored what I set and was again *huge*... 

In the Settings -> Display only lists "Default" and 320x230 ... How do I set the resolution higher so I can install? Thanks!

L. Lloyd

Oh! It would probably help... This system is a DOS game box (kinda stuck on it for the moment, the main computer is down due to a hardware failure) so it has a Voodoo 3 3000 16mb video card plugged into a 19" WS flat panel monitor. In Win98SE I use 1280x1024 resolution with large fonts and it's not bad. That's what I used when I pressed "F4" at the initial boot screen.

HI and welcome, if you cannot change the resolution you may try and use the alt key and single click and hold with the mouse and move the window to select the button. You can also try and use the alternate cd as it is a text installer.

---

### Post by llloyd on 2008-07-06
Hi! Me again. I got Xubuntu installed via the alternative cd. STILL having issues with resolution on the new install... The max it's allowing me is 800x600, at which the text is still huge and the windows still hanging off the bottom of the screen. I know the Voodoo 3 can go up to 1280x1024, it's what I use in Win98SE. How do I configure this to use that resolution? Thanks!

L. Lloyd

> **overdrank said:**
> HI and welcome, if you cannot change the resolution you may try and use the alt key and single click and hold with the mouse and move the window to select the button. You can also try and use the alternate cd as it is a text installer.

---

### Post by overdrank on 2008-07-06
> **llloyd said:**
> Hi! Me again. I got Xubuntu installed via the alternative cd. STILL having issues with resolution on the new install... The max it's allowing me is 800x600, at which the text is still huge and the windows still hanging off the bottom of the screen. I know the Voodoo 3 can go up to 1280x1024, it's what I use in Win98SE. How do I configure this to use that resolution? Thanks!

L. Lloyd

Hi and you may try and use the alt, F2 keys and enter the command 
```
gksu displayconfig-gtk
``` There you can try and set your resolution and graphics driver.

---

