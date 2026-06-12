---
title: "mic stopped working"
date: 2009-10-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by libihero on 2009-10-16
the mic on my laptop was working on karmic, and now it suddenly stopped

---

### Post by Ric_NYC on 2009-10-16
Try this:
 
Right click on the speaker icon on the taskbar>Sound Preferences>Input>Connector>Select microphone 2>Close.


See if it works now.

---

### Post by libihero on 2009-10-16
i dont see "connector"...

---

### Post by jblackhall on 2009-10-16
On the hardware tab, choose the appropriate device (likely Internal Audio in your case unless you have a separate sound card installed) and make sure you choose a Profile with "+ Analog Mono Input" at the end.  E.g. "Analog Stereo Output + Analog Mono Input"

---

### Post by libihero on 2009-10-16
none of them have mono input :(

---

### Post by libihero on 2009-10-18
bump
it WASSS working, now it doesnt
it only has stereo input, and i tried for all the different hardware combos and it wont work
is there any way that i can just restore it to complete default?

---

### Post by godhika on 2009-10-18
I encountered exactly the same problem. I think it was due to some pulseaudio update ca. 10 days ago, but I could*nt restore it either

---

### Post by libihero on 2009-10-23
bump...

---

### Post by libihero on 2009-10-23
I made a live cd of the 36 bit version of karmic rc for my brother, and i tried it out on my laptop.  the mic worked.
i remember i once did a partial update (before i saw the warning not to), could that have messed up my sound?? should i just reinstall karmic so it works again?

---

### Post by godhika on 2009-10-23
I did a new and fresh install of Karmic and now the internal mic is back - so at least for me that was the way to go.

---

### Post by libihero on 2009-10-26
ok....
so i reinstalled karmic.
mic started working again.
and now it stopped.....
this really sucks.  my mic didnt work on the earlier distros either, but at least my webcam did.... now my mic and webcam dont work lol

---

### Post by libihero on 2009-10-28
no idea why an upgrade would stop the mic from working?

---

