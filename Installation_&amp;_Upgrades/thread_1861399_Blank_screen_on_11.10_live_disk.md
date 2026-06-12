---
title: "Blank screen on 11.10 live disk"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by higashi on 2011-10-15
I'm trying to install ubuntu11.10 via USB. When I boot from the USB to try it without installing, all i get is a blank screen (I'm pretty sure what's happening is that there is no backlight so i just can't see anything)

I had the same problem with every version of ubuntu on this laptop (Gateway nv7915u). In 11.04 this was fixed by closing the screen and then opening it again and then was fixed permanently by manually installing a [patched kernel]("https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight"). This kernel fixed the lack of a backlight and also allowed me to adjust the brightness (without it, even after closing and opening the screen, i wasn't able to adjust brightness).

Here's where I need help:
I'm not sure how to go about installing 11.10. I guess I can just install without choosing to try it out first, but I don't want to risk starting up my computer and not being able to see anything at all (maybe closing and opening the screen won't work this time around) because I wouldn't be able to install the patched kernel if i can't see what i'm doing.

---

### Post by higashi on 2011-10-15
PS: I have a windows partition, so if I install it and can't see anything, would it be possible to somehow fix from the windows partition? (i.e. can I somehow install the patched kernel from windows?)

---

### Post by higashi on 2011-10-16
Bump

---

### Post by higashi on 2011-10-17
bump

---

### Post by ubu_dynamite on 2011-10-17
You could try with "nomodeset"
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

