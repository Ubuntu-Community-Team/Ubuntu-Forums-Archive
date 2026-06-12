---
title: "VAIO V505 -&gt; warty -&gt; hoary -&gt; Breezy"
date: 2005-10-21
forum: Installation &amp; Upgrades
---

### Post by dianna_wills on 2005-10-21
Few months ago, I started with warty and upgrade to hoary. There's no  problem with that. Things start falling apart when I upgrade to breezy.

GDM failed on start; and once the screen turns into "I will disable XServer for now" or something like that; **it starts to hang**.

Is there in anyway to disabled GDM and starts on to Ubuntu on text mode so I could modify xorg.conf?

I did try to run the Ubuntu LiveCD, the monitor's detection is not properly done (the images/screen is moving vertically). I was thinking of using livecd to bypass the gdm problem and get into the files and modify it from there.

But I can't. I want to know how I could run Ubuntu (Kubuntu) on a text mode.

---

### Post by Jenda on 2005-10-21
Did you try Ctrl+Alt+F1? That should switch you to console mode tty1. Once you fix what you need, do ```
sudo etc/init.d/gdm restart
```
You might have to press Ctrl+Alt+F7 to switch back to tty7.

---

### Post by dianna_wills on 2005-10-21
Ctrl+Alt+F1 does help but the keyboard wasn't properly detected at that point (or was it because it starts to 'properly' hangs at that point). What I did was try all the combinations of ctrl + shift + =  for scrolling down and suddenly it got back on again.

External Keyboard might have helped at that point. But things were properly fixed when I got to the text-mode login screen.

Thanks (^__^).

---

### Post by Jenda on 2005-10-22
Wow. Glad it helped.

---

