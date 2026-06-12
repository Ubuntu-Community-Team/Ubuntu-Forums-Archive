---
title: "No speaker icon"
date: 2010-02-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jerrynewt on 2010-02-28
For about the last two weeks I haven't had my speaker icon or battery status next to my network icon in my status bar. The only way I can change the volume is with the slide control on the top of my keyboard (HP Pavillion dv9500 - 64 bit 10.04) so I can no longer right click for sound preferences. Just wondering if anyone else has this problem?

---

### Post by sparker256 on 2010-02-28
> **jerrynewt said:**
> For about the last two weeks I haven't had my speaker icon or battery status next to my network icon in my status bar. The only way I can change the volume is with the slide control on the top of my keyboard (HP Pavillion dv9500 - 64 bit 10.04) so I can no longer right click for sound preferences. Just wondering if anyone else has this problem?

On my 64 install I do have the icon but it does not display the output correctly.

Bill

---

### Post by Uncle Spellbinder on 2010-02-28
> **sparker256 said:**
> On my 64 install I do have the icon but it does not display the output correctly.
On my 32 bit install, it shows. But it shows as muted and cannot be changed. Though sound seems fine.

---

### Post by castrojo on 2010-02-28
Make sure you have indicator-sound installed and check to see if the indicator applet is on your panel (right click on the panel, add ...)

---

### Post by n0dix on 2010-02-28
> **jerrynewt said:**
> For about the last two weeks I haven't had my speaker icon or battery status next to my network icon in my status bar. The only way I can change the volume is with the slide control on the top of my keyboard (HP Pavillion dv9500 - 64 bit 10.04) so I can no longer right click for sound preferences. Just wondering if anyone else has this problem?

If you have this kind of error in Ubuntu 10.04 is better to do a report of this, because the alpha version of Ubuntu.

---

### Post by brownknight on 2010-02-28
I have the same issue. Also, I noticed that the notification applet grows in space???

---

### Post by gotsanity on 2010-02-28
from what I have found the speaker section is just muted (the applet is still missing) I was able to adjust the sound by using alsamixer from the shell.

---

### Post by VMC on 2010-02-28
> **jerrynewt said:**
> For about the last two weeks I haven't had my speaker icon or battery status next to my network icon in my status bar. The only way I can change the volume is with the slide control on the top of my keyboard (HP Pavillion dv9500 - 64 bit 10.04) so I can no longer right click for sound preferences. Just wondering if anyone else has this problem?

We had this issue come up a week or so ago, but there has been several indicator-applets that fixed mine. When was the last time you updated?

---

### Post by garvinrick4 on 2010-02-28
Same here applet problems in notification area.

I always go System/Pref/keyboard shortcuts  and make Volume down F11 and 
Volume up F12 and use them for sound if needed when in Alpha's or Beta's when
things get a little off. And you can make a gnome-volume-control applet on bar to manage
sound preferences.

---

### Post by jerrynewt on 2010-03-01
Ok, reinstalled indicator-sound and fixed the problem. Other than that Lucid seems to be working very well so far -- gonna be a good one from what I can tell so far.

---

### Post by cyberkilla on 2010-03-02
If you are using the Staccialla (?) session, it WILL NOT show any of the "indicator-applet", "sound-applet" stuff. Fair enough, it's supposed to be vanilla GNOME.

However, shouldn't vanilla GNOME have the *original* volume applet in the notification area? I have to keep adding it myself:

```
gnome-volume-control-applet &
```

Pretty minor issue really. I'm sure they'll be able to fix it in time.

---

### Post by Uncle Spellbinder on 2010-03-02
> **jerrynewt said:**
> Ok, reinstalled indicator-sound and fixed the problem.

Indeed it did. Thanks.

---

### Post by cyberkilla on 2010-03-04
Anyone using the stracciatella session and having no volume icon? Is there a bug report on this already? I can't seem to find one myself.

---

