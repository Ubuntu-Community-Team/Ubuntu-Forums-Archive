---
title: "Sound  issues"
date: 2008-10-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by alphacrucis2 on 2008-10-13
I hadn't tested any audio since I last looked it was working with alpha 4. Now Exaile and VLC work fine but Rythembox and Totem are no longer working. May have been something I did of course. I guess the issue is related to pulseaudio. I seem to have version 0.9.10. In the gnome sound preference, settings are specified as autodetect. Clicking test I get:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

I presume this is some sort of configuration issue assuming the version I have is ok.

Any ideas?

---

