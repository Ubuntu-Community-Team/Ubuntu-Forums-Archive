---
title: "Get gnome-bluetooth to use A2DP?"
date: 2009-08-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Sam Lars on 2009-08-29
My headset was set up so easily in Karmic with gnome-bluetooth, very nice.
However, it uses the lower quality format instead of the higher one. I know with bluez-gnome I had to make a ~/.asoundrc with something like this in it:
```
pcm.bluephones {
        type bluetooth
        device 00:00:00:00:00:00
        profile “hifi”
}
```
Is there something like that for gnome-bluetooth, or how can I tell it to not use the low-quality sound?

---

### Post by benmoran on 2009-08-29
Right-click on the icon and select Sound Preferences. Then on the Hardware tab, click on your bluetooth device. You can change the profile at the bottom to A2DP. 

You *are* using Karmic aren't you?

---

### Post by Sam Lars on 2009-08-29
Yes, I didn't think to look in the audio properties. I'm still getting used to that. Thanks!

---

