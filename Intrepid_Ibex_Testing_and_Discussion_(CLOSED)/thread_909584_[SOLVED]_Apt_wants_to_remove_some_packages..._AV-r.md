---
title: "[SOLVED] Apt wants to remove some packages... AV-related stuff"
date: 2008-09-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ViRMiN on 2008-09-03
I can't for the life of me remember where to check on these changes but, does anyone have any view on whether this is a natural evolution or, whether it's purely down to the newer versions being unavailable yet and I should wait:

```
The following packages will be REMOVED
  libavcodec1d libavformat1d liblame0
The following NEW packages will be installed
  libmp3lame0
The following packages will be upgraded:
  debianutils gstreamer0.10-plugins-ugly-multiverse mplayer
3 upgraded, 1 newly installed, 3 to remove and 0 not upgraded.
```

---

### Post by Nullack on 2008-09-03
The lame packaging has changed

---

### Post by ViRMiN on 2008-09-03
> **Nullack said:**
> The lame packaging has changed

Ah, cool.  Where can I check on things like that then?  Usually, I just go to Synaptic and update stuff that doesn't want to remove other packages... at least for a couple of weeks anyway.

I thought the lame libs looked safe but, doubted the libavcodec1d and libavformat1d change...

---

### Post by Nullack on 2008-09-03
You can subscribe to the Intrepid changes mailing list -  intrepid-chang

Also on the build farm you can select individual servers and see the build history:

[https://launchpad.net/+builds](https://launchpad.net/+builds)

---

### Post by ViRMiN on 2008-09-03
> **Nullack said:**
> You can subscribe to the Intrepid changes mailing list -  intrepid-chang

Also on the build farm you can select individual servers and see the build history:

[https://launchpad.net/+builds](https://launchpad.net/+builds)

Aye, I'm already on the mailing list... maybe I need to read it more closely!?  Thanks for the advice re: the build farm. :)

---

