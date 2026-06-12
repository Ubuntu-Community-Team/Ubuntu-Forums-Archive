---
title: "kubuntu desktop-effects"
date: 2008-10-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by secret_force on 2008-10-11
I just did a fresh install of kubuntu daily (11-10), when I tried to turn on desktop-effects (they weren't turned on automatically as the release announcement said) the screen went black and now my installation is useless. Whenever I try to login to x again the screen goes either black or blank:(.
 I already logged in console mode and run 

sudo dpkg-reconfigure kdm
sudo dpkg-reconfigure kubuntu-desktop
sudo dpkg-reconfigure kwin
sudo dpkg-reconfigure kdm
sudo dpkg-reconfigure -phigh xserver-xorg

nothing worked, what else can i do?

---

### Post by ToasterThief on 2008-10-11
Doesn't:
```

sudo dkpg-reconfigure kdm kdesktop

```
work for you?

---

### Post by secret_force on 2008-10-12
I don't know if it works because I already installed kubuntu again. However I think I have to make a bug report out of this, but how??

launchpad.ubuntu.com doesn't make sense because first I don't know the exact package and second the website is just too complicated. So i never know whether it's a double post or anything. Is there another website to post bugreports?

---

