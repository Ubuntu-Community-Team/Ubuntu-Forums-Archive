---
title: "[SOLVED] Upgrading to Gutsy lagged my screen; help!!"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by TooRight on 2007-12-30
I just upgraded from Fiesty to Gutsy, have an ATI graphics card and my screen, though it appears okay at first glance, is messed up! 

First off, when I sign in, the cursor is an outlined "x" in the middle of the screen, and the halves of the screen in diagonals from it flash from golden-brown to black rapidly.
My desktop seems normal, however my icons in my task bar flash black backgrounds when clicked. When firefox is opened (had to delete its profile.ini first before it would load), it opens slowly, but appears fine. it takes foreverrrr to scroll up and down pages and it doesn't do it smoothly at all. 

It has to be my xorg.conf and that damned ati card, but i can't for the life of me figure out what exactly needs fixing... I even went in and set Composite to "Disable". Do any of you have any ideas? I'm trying to read various threads in here, but with the pages scrolling so slowly, it's a real b*tch!! lol

---

### Post by taurus on 2007-12-30
Maybe you need to reconfigure the X server again.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Restart X with <Ctrl><Alt>Backspace.

---

### Post by TooRight on 2007-12-30
Just tried that after reading your post and it tells me "xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20071229223740" and then is done. When I restart X, there's no change :(

---

### Post by taurus on 2007-12-30
Which video driver are you using now?  Have you tried to install an ATI driver for it?

```
cat /etc/X11/xorg.conf
```

---

### Post by TooRight on 2007-12-30
Woo hooo!! That did it... omggg, I could kiss you right now, scroll is fixed, black flashes behind the taskbar icons are gone... hmmm.. seem to be having a problem with a really bad lag on my keystrokes though, but it's alot better than it was before!! Will try to find a solution for that now!! Thankies!!!

---

### Post by TooRight on 2007-12-30
Okay, to solve the keystrokes problem i followed the directions [here]("http://ubuntuforums.org/showpost.php?p=3547899&postcount=8") to completely get rid of compwiz and xgl from my system.That did the trick, and my system is running perfectly fine... I loveee Gutsy!! I can even watch divx movies, right on the browser :o !!

Later on I'll worry about getting the fancy effects, for now I'm just thrilled to enjoy my new and improved Ubuntu!! :)

Thanks again Taurus!! :)

---

### Post by taurus on 2007-12-30
> **TooRight said:**
> Woo hooo!! That did it... omggg, I could kiss you right now, scroll is fixed, black flashes behind the taskbar icons are gone... hmmm.. 

Easy there, tiger.  And you're welcome.

---

