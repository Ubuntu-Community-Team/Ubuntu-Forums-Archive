---
title: "Medibuntu - is it ready for Karmic?"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by emarkay on 2009-10-05
This adds more "non-free" codecs and the like to the default installation.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Just want to confirm - it says here: 
[http://packages.medibuntu.org/](http://packages.medibuntu.org/)
it was added in May of this year, but haven't seen a confirmation here via search.

Thanks

---

### Post by slakkie on 2009-10-06
I have medibuntu's repository in my sources.list, don't know if I have packages installed from them tbh.

I just checked:

```

http://packages.medibuntu.org karmic/non-free            libamrnb3                           7.0.0.2-0.1medibuntu1
http://packages.medibuntu.org karmic/non-free            libamrwb3                           7.0.0.3-0.0medibuntu1
http://packages.medibuntu.org karmic/free                libdvdcss2                          1.2.10-0.3medibuntu1
http://packages.medibuntu.org karmic/non-free            non-free-codecs                     4medibuntu1
http://packages.medibuntu.org karmic/non-free            w32codecs                           20071007-0medibuntu5

```

---

### Post by oboedad55 on 2009-10-06
> **slakkie said:**
> I have medibuntu's repository in my sources.list, don't know if I have packages installed from them tbh.

I've got it my repos and programs installed from them. It seems fine to use with karmic.

---

### Post by wilee-nilee on 2009-10-06
> **oboedad55 said:**
> I've got it my repos and programs installed from them. It seems fine to use with karmic.

Same here I can play dvd's and all the usual suspects of media types, avi,flv,wmv--etc

---

### Post by dalonso on 2009-10-06
> **wilee-nilee said:**
> Same here I can play dvd's and all the usual suspects of media types, avi,flv,wmv--etc

I do not have Medibuntu enabled and I can play DVD's as well. The support for DVDs is now in universe (libgstdvdspu and libresindvd plugins), installing the gstreamer-plugins-bad. It seems to work fare well.

As for the other codecs, I have just to find a video not playing fine with the codecs included in gstreamer-plugins-bad and gstreamer-plugins-bad-multiverse.

---

### Post by andrew.46 on 2009-10-06
Medibuntu has been working fine for me under Karmic although I have only installed the w32codec pack. Of special interest with the Karmic offerings is that the Medibuntu MPlayer has been withdrawn, I suspect that this is a vote of confidence in the much improved and modernised MPlayer seen in Karmic.

Andrew

---

