---
title: "Install Succesful, but more problems..."
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by chrini on 2007-09-25
Ok, I posted a forum a couple weeks ago about problems with the installation of Ubuntu... and thanks to everyone's help I have it successfully installed.... 

Now, it loads up just fine (at least it appears to load up fine) and right after it has loaded (this is the first Ubuntu logo you see, where the orange loading bar is) I see a black screen with the Ubuntu logo blurred across the bottom and then I finally see the orange Ubuntu backround... however, shortly after I see the orange background, the OS freezes up... I don't even get to the sign in potiton.... Any Ideas?

---

### Post by chrini on 2007-09-25
Ok, so on load up I moved the mouse continuosly (why this would help, I'm not sure) and it loaded up fine... however, now on the desktop I am seeing a lot of "shadows" from the previously opened menus, windows, etc... and the pixelation, etc, just isn't right.... I think I might have an issue with vid card. Is that what other people might suspect?

---

### Post by zvacet on 2007-09-25
If it is video card you can try this

```
sudo dpkg-reconfigure xserver-xorg
```

and pick **vesa**.

After that go and find driver for your card.When you find it and install run again upper command and now pick your card.

---

