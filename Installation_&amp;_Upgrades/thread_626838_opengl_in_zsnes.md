---
title: "opengl in zsnes"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by adamb23 on 2007-11-29
yes im using ubuntu gutsy 7.10 and any time i load one of the opengl option in zsnes 1.51 it runs seriously slow. Can anyone help?

---

### Post by twist2b on 2007-11-29
zsnes is instant for me..... but heres what you should do.....
check if theres any updates for your graphics card..... im sure its not a NVIDIA otherwise you would be fine....
but after that no luck then just use snes9x
snes9x isnt as pritty but its better (i think)
that should work for you :)

---

### Post by atlfalcons866 on 2007-11-29
you might not have direct rendering on

to find out what you get go to the terminal and type

> glxinfo | grep render

---

### Post by adamb23 on 2007-11-29
it says i dont have it turned on how do i turn it on?

---

### Post by atlfalcons866 on 2007-11-30
whats your video card?

post your lspci in the terminal

> lcpsi

---

### Post by adamb23 on 2007-11-30
ati radeon 9800 pro 128mb

---

### Post by atlfalcons866 on 2007-11-30
did you install the restricted driver?

go to system>system>Restricted drivers manager

---

### Post by adamb23 on 2007-11-30
ya i installed it through envy

---

### Post by adamb23 on 2007-12-01
and the driver is enabled in the restricted drivers manager

---

### Post by dfreer on 2007-12-09
What does this command return:
```
glxinfo | head
```
I'm willing to bet that your drivers just aren't installed/configured correctly.

---

