---
title: "How to play dvds on ubuntu 10.04?"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by TheNerdAL on 2010-04-10
I want to be able to play DVD's from my computer but I can't, how do I do it? Thanks!

---

### Post by andrewabc on 2010-04-10
One way is to install VLC.

There are plugins for default totem, but I forget which ones.

EDIT:
dvd playback not in by default because it is proprietary and costs money to license. unless I'm mistaken.

---

### Post by TheNerdAL on 2010-04-10
VLC doesn't show video, I think it thinks it's a cd. Help!
How do I make it default?

---

### Post by !@!@! on 2010-04-10
Try installing libdvdcss if you don't have it.

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Also, it may help to install the restricted/ugly/bad formats.

```
sudo aptitude install gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
```

---

### Post by ELD on 2010-04-10
No offense but if you cannot help yourself with a simple issue like this you shouldn't be using the development release. Stuff like this is better suited to a stable release.

Have you installed the restricted extras which includes libdvdcss for the dvds.

---

### Post by TheNerdAL on 2010-04-10
> **ELD said:**
> No offense but if you cannot help yourself with a simple issue like this you shouldn't be using the development release. Stuff like this is better suited to a stable release.

Have you installed the restricted extras which includes libdvdcss for the dvds.

Dude, this is the forums, where people ask for help and stuff. I installed Beta 1 to help the Ubuntu team with bugs and issues and stuff.

---

### Post by TheNerdAL on 2010-04-10
> **!@!@! said:**
> Try installing libdvdcss if you don't have it.

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Also, it may help to install the restricted/ugly/bad formats.

```
sudo aptitude install gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
```

Thanks! It works! :D

---

### Post by !@!@! on 2010-04-10
> **TheNerdAL said:**
> Thanks! It works! :D
Glad I could be of assistance! ;D

You are the first person I ever helped. :P

---

### Post by ELD on 2010-04-10
> **TheNerdAL said:**
> Dude, this is the forums, where people ask for help and stuff. I installed Beta 1 to help the Ubuntu team with bugs and issues and stuff.

Yes this is a forum, but this is the lucid testing forum, a simple thing like playing dvds could be helped elsewhere by the many many tutorials and how-tos already available, also note the sticky topics where there is a nice big image telling you to use the search.

Anyway i'm glad the issue has been solved.

---

### Post by dcstar on 2010-04-10
> **eld said:**
> yes this is a forum, but this is the lucid testing forum, a simple thing like playing dvds could be helped elsewhere by the many many tutorials and how-tos already available, also note the sticky topics where there is a nice big image telling you to use the search.


+1

---

### Post by Captain_Kirk on 2010-04-10
> **ELD said:**
> Yes this is a forum, but this is the lucid testing forum, a simple thing like playing dvds could be helped elsewhere by the many many tutorials and how-tos already available, also note the sticky topics where there is a nice big image telling you to use the search. 

True... if the question at least would have been about how to play (commercial) bluerays... :popcorn:

---

