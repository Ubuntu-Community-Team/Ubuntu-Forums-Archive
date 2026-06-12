---
title: "is Gnash working with Lucid ?"
date: 2010-03-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dino99 on 2010-03-08
My logs are flooded with "Xid collision" if i use Shockwave. So i've removed/purged all related packages.

Are you using Gnash with success on Lucid ?

[https://bugs.launchpad.net/firefox/+bug/401823](https://bugs.launchpad.net/firefox/+bug/401823)

---

### Post by seeker5528 on 2010-03-08
> **dino99 said:**
> My logs are flooded with "Xid collision" if i use Shockwave. So i've removed/purged all related packages.

Are you using Gnash with success on Lucid ?


Any time I have tried Gnash, it has not really seemed to be much use. Tried it a couple of weeks ago on Lubuntu because it was pulled in by dependencies. 

I think swfdec isn't intended to be as complete of an implementation of Flash as Gnash, but it seems to work with more stuff on the web than Gnash whenever I have compared the two, have not tried it for a while.

On my Lubuntu install I left the main Gnash stuff on there because of dependencies, but removed the browser plugin because even after installing Flash, then going into the firefox addons and setting Gnash to disabled, it still was preventing Flash from working.

Later, Seeker

---

### Post by psyke83 on 2010-03-08
Gnash seems to require extra packages in order to play videos on sites such as Youtube (I believe it's gstreamer0.10-ffmpeg, or something similar). However, not all videos will work even with all the necessary codecs installed.

EDIT: Correction, I meant "gstreamer0.10-gnomevfs".

---

### Post by dino99 on 2010-03-09
Some troubles to install it, have manually installed every packages requested by gnash, but still says: might not be installed.
So, there are conflicts somewhere. Can't find recent doc or howto about gnash.

---

### Post by psyke83 on 2010-03-09
> **dino99 said:**
> Some troubles to install it, have manually installed every packages requested by gnash, but still says: might not be installed.
So, there are conflicts somewhere. Can't find recent doc or howto about gnash.

What package are you installing? The "mozilla-plugin-gnash" package is what you want (though you also need gstreamer0.10-gnomevfs for Flash video, and possibly the codecs from ubuntu-restricted-extras).

Maybe it's something simple, such as not having the universe repository enabled.

---

### Post by dino99 on 2010-03-09
mozilla-plugin-gnash:
 Dépend*: gnash mais ne doit pas être installé

gnash-common:
 Dépend: libboost-date-time1.40.0 (>=1.40.0-1) but it is not installable
 Dépend: libboost-thread1.40.0 (>=1.40.0-1) but it is not installable

gnash:
 Dépend*: gnash-common mais ne doit pas être installé

here are the output: might not be installed

all repo activated and workaround like apt-get install -f dont return error.

---

### Post by dino99 on 2010-03-10
ok now i can install it with the latest updates, maybe some misconfig on my end.

---

