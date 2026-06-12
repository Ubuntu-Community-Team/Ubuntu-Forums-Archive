---
title: "dvd playback color problem in hardy"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by bodhidharma on 2008-05-12
I recently upgraded to Hardy... and now, on random occasions,
I get this weird thing with colors being reversed in DVD playback.
The machine is a Thinkpad R61e, I'm fairly experienced, the upgrade
went well, the playback software I'm using is VLC... quite odd the
way this is *not* a consistent thing, sometimes when I reboot after
a day of doing other things and try the very same DVD, it works!

Any ideas, guri out there?

Thanks!

---

### Post by amohanty on 2008-05-12
You could try running VLC from the command line and see if there are any relevant messages when the reverse-video thing happens. FWIW I use VLC on a T60 and have never had any trouble.

AM

---

### Post by peitschie on 2008-05-12
Check my reply here: [http://ubuntuforums.org/showpost.php?p=4938996&postcount=2](http://ubuntuforums.org/showpost.php?p=4938996&postcount=2)

Though the inconsistent nature does seem odd... it might be connected to if you listen to music etc. or use the GStreamer backend prior to launching VLC.  See if when the colours are inverted your XV_HUE is set to like 178 or something...

---

### Post by ab636 on 2008-08-07
even if I change 179 to 0 - the color is the same, in any application

---

### Post by peitschie on 2008-08-07
What's the output of both when the colour is normal, and when the colour is inverted?
```

xvinfo | grep -A2 XV_HUE
```

---

