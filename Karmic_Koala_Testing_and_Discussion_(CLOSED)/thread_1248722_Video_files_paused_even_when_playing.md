---
title: "Video files paused even when playing"
date: 2009-08-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tuppe666 on 2009-08-24
I have media player that up until about a week ago played everything. It says its playing...but it is paused a can seek though the video to look so its clearly there. It says its playing...but isn't.

---

### Post by taavikko on 2009-08-24
Little more info on the issue is always a good idea.

what mediaplayer?
what video-chip/driver?

CLI output ?

---

### Post by JohnJackson on 2009-08-24
I had a similar problem which was 'fixed' by killing pulseaudio. It may or may not be the same problem.

---

### Post by tuppe666 on 2009-08-25
Using integrated Intel graphics+add2 card
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation 82915G Integrated Graphics Controller (rev 04)

Totems output is:
Fatal Python error: PyEval_SaveThread: NULL tstate
Aborted (core dumped)

---

### Post by taavikko on 2009-08-25
Try booting with "nomodeset" if that clears the issue.
Older intel chips are a bit of a mess currently...

---

### Post by tuppe666 on 2009-08-25
I have to boot with nomodeset as default anyway, otherwise it does not pick up my TV which is a pain. The problem does seem to be pulseaudio related, as the last update plays a little tiny bit jumpy and then announces pa stream unittable  size failed or something similar its difficult to make out. Thank you for trying though

---

