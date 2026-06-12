---
title: "Weird Text In Google Earth"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by Dusty2711 on 2010-12-28
Hey guys! Just installed the new google earth. I had some errors trying to get it to start but I got that fixed. But when it opens all works but the text is really weird and just in strait lines!! What is this? And how can I fix it?

[IMG]http://img251.imageshack.us/i/greattheme3.png/[/IMG]

If the image does not show up just go to [http://img251.imageshack.us/i/greattheme3.png/](http://img251.imageshack.us/i/greattheme3.png/)
Here is what it looks like.

---

### Post by Entropy512 on 2011-01-12
Exact same problem here.
Kubuntu 10.10 x86-64

NVidia GTX460

I tried some of the Google Earth "font fix" tutorials that replace a bunch of Qt libraries, however, these tutorials don't work for x86-64 due to lack of a 32-bit libQtWebKit.so.4

---

### Post by Entropy512 on 2011-01-16
For me, this solved the problem:
sudo apt-get remove ttf-mscorefonts-installer
sudo apt-get install ttf-mscorefonts-installer

(i.e. remove and reinstall the MS Core Fonts)

---

### Post by pchev on 2011-02-15
Thank you!

I have the same problem and it is solved after reinstalling mscorefonts.

---

### Post by def670 on 2011-09-17
awesome!  you fixed the issue completely! thanks so much

---

