---
title: "dirty but effective gdm/ldm/xdm background changer"
date: 2012-03-18
forum: Installation &amp; Upgrades
---

### Post by boblizar on 2012-03-18
after fighting with LDM and broken apps on ubuntu 12.04, i decided to go straight for the kill.  simply symlink your picture

sudo mv /usr/share/backgrounds/warty-final-ubuntu.png /usr/share/backgrounds/warty-final-ubuntu.png.backup

sudo ln -s $HOME/Pictures/backgrounds/space/2-1920x1080.png /usr/share/backgrounds/warty-final-ubuntu.png

just open a jpeg in gimp, and save as samefile.png and point a symlink at the picture. mine happens to be in $HOME/Pictures/backgrounds/space

---

### Post by bobb40 on 2012-04-28
> **boblizar said:**
>  ...simply symlink your picture to .../warty-final-ubuntu.png

I always did it that way before 12.04, except I just linked my jpg to warty...png. But 12.04 insists the target be a png also, so I converted my picture with "convert mypic.jpg mypic.png", using an ImageMagick utility.

---

