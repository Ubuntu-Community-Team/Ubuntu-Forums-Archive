---
title: "Installing restricted drivers causes blank screen at startup"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by jroach on 2008-04-11
Hey guys,

I'm trying so hard to get my graphics card working. I just installed 7.10. the installation went fine. i got all updates, and enabled restricted drivers. well now every time i start it up, my bios posts, then i see a blurred image of the ubuntu loading screen for half a second, then the screen goes blank and nothing appears on it until i restart again. the only way i can get into my desktop and see it is if i screw things up in the xorg reconfigurer in recovery mode and start up in low graphics mode.

I'm tried eliminating all resolutions i don't want in both the reconfigurer and the xorg.conf file, as well as adding the line "option "UseDisplayDevice" "DFP"" to xorg.conf. nothing seems to work

I'm using an ati hd2900 xt, and my screen is a syntax-olevia 27" lcd tv.

i'm at my wit's end, any ideas?

---

### Post by Pumalite on 2008-04-11
ATI doesn't support Linux. In general I've seen people do better with 'vesa' than with the ATI driver. You could try ENVY before giving up (Envy is a shot in the dark; some people do great; others not so):
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by jroach on 2008-04-11
alright, does anyone else have any ideas so that the screen doesn't go blank when using my proprietary drivers?

---

### Post by warp99 on 2008-04-11
> **jroach said:**
> Hey guys,

I'm trying so hard to get my graphics card working. I just installed 7.10. the installation went fine. i got all updates, and enabled restricted drivers. well now every time i start it up, my bios posts, then i see a blurred image of the ubuntu loading screen for half a second, then the screen goes blank and nothing appears on it until i restart again. the only way i can get into my desktop and see it is if i screw things up in the xorg reconfigurer in recovery mode and start up in low graphics mode.

I'm tried eliminating all resolutions i don't want in both the reconfigurer and the xorg.conf file, as well as adding the line "option "UseDisplayDevice" "DFP"" to xorg.conf. nothing seems to work

I'm using an ati hd2900 xt, and my screen is a syntax-olevia 27" lcd tv.

i'm at my wit's end, any ideas?

Do you see the splash screen or just not the login screen?

---

