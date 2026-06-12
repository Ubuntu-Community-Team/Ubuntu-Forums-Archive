---
title: "installed 7.1 but all i get is completely black screen"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by ReillyRoo on 2008-01-24
my machine:
amd 64 x2 2.8ghz cpu
2gb ram
2x  nvidia 8600 gt  graphics cards
160gb hard drive


i could never properly run the regualar cd so i installed ubuntu 7.1 with the aleternate (Text based) cd and then restarted my computer. i get the ubuntu splash screen and the orange loading bar and then... nothing... blacknss... forever.  if it doesnt work on nvidia 8600 gt cards... then what the hell does it work on?

im very very upset because it works perfectly on my laptop so i know its not the installation cd.

---

### Post by taurus on 2008-01-24
Press <Ctrl><Alt>F2 to get to another console.  Log in with your username and password.  Then, reconfigure your X server again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Make sure you choose either **nv** or **vesa** driver for your graphic card for now, not nvidia.  Then, get back to the GUI login screen with <Alt>F7 and restart X again with <Ctrl><Alt>Backspace.

---

