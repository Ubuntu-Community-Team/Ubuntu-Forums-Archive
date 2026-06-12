---
title: "Problem after installing Ubuntu on a G3 iBook"
date: 2006-02-28
forum: Installation &amp; Upgrades
---

### Post by simplemind7 on 2006-02-28
hello, i just installed ubuntu onto my G3 iBook and it seemed to install fine, but now it doesn't load properly and i can't figure out why.

after it loads up and i type in my login and password, it just goes to the brown screen and stops, then does nothing, i can get into the command prompt from there, but that is all.

any ideas?

---

### Post by stuporglue on 2006-02-28
A couple ideas. These are more either-or, not both at the same time...

1) Go to a command prompt. log in and type "dmesg". see if anything suspect gets printed to the screen. 

2) Try starting X manually
log in at the prompt. stop the login manager:
```
sudo /etc/init.d/gdm stop
```

try to start X manually:
```
startx
```

3) Try reconfiguring your screen
log in:
```
sudo dpkg-reconfigure xserver-xorg
```

Restart the login manager
```
sudo /etc/init.d/gdm restart
```

Good luck!

---

### Post by simplemind7 on 2006-02-28
i tried 3 already, i found that from a search of this site, but it didn't work for me.

tried #1 just now, and it comes up with a list of things, it seems like a list of things that last happened or something (i'm kind of new to linux) and i don't know what i'm looking for in the list, so i just went a tried #2

when i type the first half of 2, the display gets screwed up, all the text gets distorted and the bottom 1/4 of the screen gets some random green blur over the distorted text, so i just typed the second half of it anyway and pressed enter, that made it go to a screen with a very small grey and black checkerboard pattern (a couple pixels each) and it has an X for the cursor... but it doesn't do anything, i just move the cursor around with the trackpad.

what do you think? :-k

---

### Post by simplemind7 on 2006-03-01
anyone?

---

### Post by linear on 2006-03-01
Have you checked for the [date bug]("https://wiki.ubuntu.com/UbuntuDateBug")?

---

### Post by simplemind7 on 2006-03-01
thank you!!!

i did not know about this, and it worked, the date was set to 1976.

works great now, thanks again :-D

---

