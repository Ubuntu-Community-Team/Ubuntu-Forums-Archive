---
title: "corrupted display when running specific programs"
date: 2009-07-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by setherd on 2009-07-23
I started up virtualbox today to run some things and as soon as the Virtualbox window to select the guest OS comes up my display gets very dark and it seems to drop down to a 16 color depth. it's totally unusable.
as soon as I close the window my desktop reverts back to normal OR if I bring another window to the front.
I initially thought it was a virtual box problem.
later I tried to run calibre (an Ebook organizer and reader) I had the exact same problem. as long as that window is in the foreground. I have a very dark and low color depth display. If I close the window or just select another open window to bring it to the front my display returns to normal.
I tried to make a screen shot but it shows everything as looking normal.

I'm not sure what either of these programs would have in common to cause this.
does anyone have any ideas?

---

### Post by l.aluffi on 2009-07-24
Seems to be related to programs using qt libraries in gnome environment: it happens too with googleearth and skype.

Maybe should be the case to open an issue in launchpad, but I have no time to gathers clues.

Could you do it?

---

### Post by setherd on 2009-07-24
thanks, I opened a bug report :)

---

