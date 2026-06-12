---
title: "snapshot"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by evilc on 2006-11-02
Is there another program like "take screenshot" that can copy part of screen only and a scrolling window?

Also I noticed in forums members paste a copy/picture of information using terminal that can scroll how can I do that? 
Thanks

---

### Post by bukwirm on 2006-11-02
Look into ImageMagick, and it's "import" command.

---

### Post by kerry_s on 2006-11-02
I use scrot to take screen shots. 
sudo apt-get install scrot
Here's the commands i use.
scrot %T.jpg    <-takes whole screen
scrot -s -b %T.jpg    <- you can select with a click or click and drag to grab a square section.
scrot -d 5 %T.jpg     <-wait 5 seconds before screenshot

---

