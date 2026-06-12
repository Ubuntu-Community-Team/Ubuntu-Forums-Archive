---
title: "Beryl on ATI X1600"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by Kurzweil on 2006-12-09
Alright, I followed the guide on enabling my card and I think it worked. The resoloution went way up and the windows all move smoothly now. I had to omit the:

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

With this in the confg, it freezes on bootup but without it seems to work great.

I installed beryl and followed the instructions to add the script to start with xgl, when it boots into that it run VERY slow and beryl will not run. Any tips please? If I get this card to work right and get beryl running, you have a full convert! :)

---

### Post by mrfuzzemz on 2006-12-09
What do you get when you enter:

```
glxinfo | grep rendering
```

Into the terminal? It is usually necessary to have the:

```
Section "Extensions"
      Option "Composite" "Disable"
EndSection
```

with an ATI card using the fglrx driver because xorg 7.1 in Edgy has composite on by default and fglrx does not support composite yet.

---

### Post by Kurzweil on 2006-12-09
Alright, reinstalling.. it decided to quit booting completely so I'm going to try again.

---

### Post by mrfuzzemz on 2006-12-09
Alright.  Just let me know what happens.  I've had to conquer many a problem with ati drivers as they are not as stable and Linux-friendly as nvidia drivers.

---

### Post by Kurzweil on 2006-12-09
thanks. if you can get me running you've got a friend for life. lol. I've been fighting this thing for two days... I put in an old nvidia card have and it worked fine but I just got the x1600 and I can't have it go to waste.

---

### Post by mrfuzzemz on 2006-12-09
Well I'm running a x1600, but mine is the mobility (for notebooks) version.  I have full support at the moment.  I've gotten XGL running smoothly on it, but I don't use it all the time because I'm waiting for AIGLX support. Hopefully *that* will come soon due to ATI being obtained by AMD.

---

### Post by Kurzweil on 2006-12-09
alright, follwed guide and when it boots, it looks good at first but when I move a window or something has to redraw, Im geting blank and clear windows that kinda disappear as I move them.

---

### Post by Kurzweil on 2006-12-09
I went back and took out

Section "Extensions"
      Option "Composite" "Disable"
EndSection


and it seems to be running fine now. Except fglrxinfo displays something about mesa3d.org  and it says extenstion "Xfree86-DRI" missing on display ":0.0".

But it is usable now. Just doomed to no beryl?

---

### Post by Kurzweil on 2006-12-09
Alright, I'll quit updating my own thread now. :)

So far, this WILL NOT work with the Composite disabled. Either wont boot or I get weird graphic artifacts. I loaded it up witht he xgl sessions and its running unusuably slow... I guess Im not really geting 3d acceleration. Maybe just 2d.

---

