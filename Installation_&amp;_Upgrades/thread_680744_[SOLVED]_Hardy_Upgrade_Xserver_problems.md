---
title: "[SOLVED] Hardy Upgrade Xserver problems"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by Achetar on 2008-01-28
Okay, so yesterday i decided to upgrade to Hardy. I didn't expect it to run very well from the start, but this is different.
Here are the symptoms of my problem:[LIST]
[*]On boot, I believe the xserver crashes (wierd display, I would get a screenshot, but I can't use any screenshot programs), although it could be gdm, I am not sure
[*]I am able to move the mouse around
[*]Ctrl+Alt+Backspace does **not** restart the X server[/LIST]I started in recovery mode and dropped into a root shell, and ran startx and it gave me the same problem. 

Any help?

---

### Post by zvacet on 2008-01-28
I don´t promise anything,but try in recovery mode

```
dpkg-reconfigure xserver-xorg
```

---

### Post by PmDematagoda on 2008-01-28
Could you also post the specifications of your PC.

---

### Post by Achetar on 2008-01-28
Alright, I fixed it, I added the following to my xorg.conf under the "Device" Section
```

Option "AGPMode" "4"

```

And now it works great!

I am playing around with the new stuff, thanks for the quick replies, even though I fixed it myself.

---

