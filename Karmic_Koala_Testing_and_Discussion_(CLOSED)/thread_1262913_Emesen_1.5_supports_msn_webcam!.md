---
title: "Emesen 1.5 supports msn webcam!"
date: 2009-09-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by puccaso on 2009-09-10
i havent tested it yet
but i installed it

it needed libmimic, which wasnt avaliable, though it seems to have been accepted into the dist, i installed it from launchpad,

it sees the cam, i just need to test it

---

### Post by kestal on 2009-09-10
> **puccaso said:**
> i havent tested it yet
but i installed it

it needed libmimic, which wasnt avaliable, though it seems to have been accepted into the dist, i installed it from launchpad,

it sees the cam, i just need to test it

Yeah, I was pretty excited about it. I tested it out before they offered the distribution packages (for ubuntu) for them when it first came out, and it worked pretty nicely.

The layout is pretty nice, too. I haven't run into many problems with it (including the old msn contact syncing problem when you added someone on emesene - all gone now).

It even worked on a computer with a webcam that Linux didn't even support at all. (only for the first time use when starting up the pc, any time after that it was all garbled - which, I think is pretty interesting)

---

### Post by tghe-retford on 2009-09-10
libmimic (which is libmimic0 and the other relevant packages) are now in the Karmic repositories, so its just a case of updating and installing from whichever package manager you use.

EDIT: You'll also need to install python-gst0.10 as well, before doing this I got an error that the webcam could not be initialised because of pygst.

---

### Post by puccaso on 2009-09-10
i think i jynxed myself.

i get the webcam video window, but i cant see my buddies webcam nor can they see mine.

---

### Post by rolandixor on 2009-09-20
I have the same issue. I can't see my webcam, even tho emesene knows it's there, and claims to turn it on (even camera monitor launches). I'll be upgrading to karmic once it's stable enough so I'll see if that changes anything, and that is if I can't get this working before.

---

### Post by Jesus_Valdez on 2009-09-20
I checked the emesene forums and they said that currently theres nobody working on the camera feature.

So, I don't expect changes soon.

---

