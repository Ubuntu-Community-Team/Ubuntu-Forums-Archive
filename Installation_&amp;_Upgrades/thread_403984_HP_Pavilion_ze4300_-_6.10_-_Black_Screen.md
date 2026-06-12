---
title: "HP Pavilion ze4300 - 6.10 - Black Screen"
date: 2007-04-07
forum: Installation &amp; Upgrades
---

### Post by jayschell on 2007-04-07
When trying to install 6.10 to my laptop, it gets to the point where it should bring up the desktop for the live CD where I can install. Instead it brings up a black screen. Anyone ever had this experience or am I just special? Thanks for the help!

---

### Post by jayschell on 2007-04-08
help?

---

### Post by slimsumo on 2007-04-22
I had the exact same problem
here is how i got it fixed

1.boot in the cd and wait for the ubuntu sound
2.type ctrl+alt+F1
3.At the prompt(ubuntu@ubuntu%)type this : "sudo nano /etc/X11/xorg.conf"
4.scroll down the text file until you find a place where it is written : driver "ati"
5.replace "ati" by "vesa"
6. press ctrl+x to exit 
7. select yes when it asks if you want to save and press enter to confirm the place(wich stays the same)
8.press ctrl+alt+f7 to go back to user interface (which is now a black screen)
9.press ctrl+alt+backspace to reset user interface
10. enjoy ubuntu

---

