---
title: "Karmic 64, latest update broke my system"
date: 2009-10-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by PendragonUK on 2009-10-15
I'm running Karmic 64 on my desktop PC, I have been checking daily for updates. All has been going well until this evening. After an large'ish update today I was instructed to reboot. After reboot Xserver doesn't start and the screen is strobing. There are partial and garbled messages on screen. It looks like it's at log in, on odd thing is that the input from the keyboard would also appear to be pulsating/flashing. To get a key press to register you have to hit it many times to catch the right moment. 

To get the computer to boot I had to select one of the earlier version at boot up.

---

### Post by sanderj on 2009-10-16
I had something like that with my Karmic (32-bit): after the update a few days ago, X or the WM was not working correctly anymore: black screen, with only a mouse pointer. No windows or bar.

I've reinstalled Karmic Beta, and won't update for some time.

---

### Post by PendragonUK on 2009-10-16
You always have to be aware that things may go wrong when using a Beta. I just thought I would let others now that there might be a problem. You never know if your on your own or one of thousands... This one looks like I'm on my own LoL

---

### Post by Guruji on 2009-10-18
you're not alone, i have the same problem.. and didn't found a fix yet, else than using vesa driver but then no compiz..

---

### Post by badook on 2009-10-18
same problem here using 32bit on a asus eee 1101HA...maybe the problem is related to the gma500? Damn why did i update :(

---

### Post by invenit on 2009-10-18
> Damn why did i update 

Do drive image backups before you experiment. That way you're only a few minutes away from your previously working setup. :popcorn:

---

### Post by badook on 2009-10-18
I guess you're right eheh...

---

### Post by darco on 2009-10-18
I just updated my laptop yesterday after having installed KK couple of weeks back. Yup broke my system too...
Logged in to the previous kernel and in dropped me into text mode. Also had to run startx to get me to the desktop. Wireless broke, touchpad broke....I was able to recover using a wired connection, usb mouse and ran update manager. Broken packages found, needed to run the sudo dpkg --configure -a and now all is good!
Good luck and dont give up

darco

---

