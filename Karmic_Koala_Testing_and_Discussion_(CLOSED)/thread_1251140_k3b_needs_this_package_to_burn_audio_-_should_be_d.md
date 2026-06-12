---
title: "k3b needs this package to burn audio - should be depends?"
date: 2009-08-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by maestrobwh1 on 2009-08-27
libk3b6-extracodes is needed to burn any audio other than *.wav.  Even though lame shows up in the configuration of k3b, it doesn't burn mp3 without this package -->  suggest making it a dependency?

---

### Post by rbmorse on 2009-08-27
The package contains some restricted codecs, so it's not going to be part of a default installation out of consideration for users who wish to use  only software distributed under open-source and free licenses. 

So, if you want to use that package you're going to have to  install it  explicitly. Fortunately, the developers have packaged  the restricted codecs so installation takes but one click. Seems like a reasonable solution to me.

---

### Post by maestrobwh1 on 2009-08-27
I mean this as an honest question: _is mp3 playback supposed to not work even if "lame" is listed as enabled under "external decoders" in k3b?_

Also, I have been using Debian/Ubuntu since Knoppix3.3 and Dapper 6.10.  I disagree that it is simple to those who want stuff to work.  Sure, it is one click, but it isn't like K3b tells a person that the package is *explicitly* is needed: There are wiki's and whatnot but even this one was off the radar.

Not everything is as simple to less seasoned users, and therefore not seemingly reasonable.

Purists.  Like people who think that insist on buying American.  Some piece of it came from somewhere else:-)

---

