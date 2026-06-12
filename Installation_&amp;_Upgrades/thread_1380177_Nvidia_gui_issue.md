---
title: "Nvidia gui issue"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by Gatch on 2010-01-13
Recently upgraded from Hardy to Jaunty. I am having a problem with changing the resolution.

Nvidia GUI recognizes my graphics card (GeForce 6200) and my monitor (Acer 191W). But it is stuck in 800 x 600. I cannot scroll down to the settings to make the necessary changes the because screen is too large.

I know I am revealing my stupidity, but I do not know enough about the xconfig file to attempt a fix. 

Any ideas?

---

### Post by fancypiper on 2010-01-13
Try moving the window either by running the mouse to the area you want to see, or drag the window with alt-left click and drag.

---

### Post by chewearn on 2010-01-13
Grab the window by ALT+LeftMouseButton to move it upwards, so you could access the bottom part.

If the window refuse to move beyond top of the screen, enter this command in a terminal:
```
gconftool-2 --set /apps/compiz/plugins/move/allscreens/options/constrain_y --type bool 0
```

---

### Post by Gatch on 2010-01-13
The ALT+LeftMouseButton did the trick! 

Thanks for both of your prompt replies.

---

### Post by fancypiper on 2010-01-13
Glad to be of help.

[Mark Your Thread as [SOLVED] After Getting Your Answer](http://ubuntuforums.org/showpost.php?p=4527051&postcount=6)

---

