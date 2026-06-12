---
title: "camera unable to mount"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by everytimeref on 2008-11-04
lots of people have had problems with digital cameras in Intrepid, specificallly camera unable to mount errors.

After some searching around I've solved this problem by updating my libgphoto 2 library.

I added these lines to Administration\ software sources:

deb [http://ppa.launchpad.net/pitti/ubuntu](http://ppa.launchpad.net/pitti/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/pitti/ubuntu](http://ppa.launchpad.net/pitti/ubuntu) intrepid main

Ran the update recommended and hey presto my Panasonic tz3 is working again.

My faith in Ubuntu is restored.

Apologies if I haven't followed any protocol posting this but it is useful...

---

### Post by Ewan the moomintroll on 2008-11-04
Excellent!
that worked perfectly for my panasonic lumix dmc-fz30, but sadly not on my hp photosmart r507, i can just swap sd card though.
it seems completely nonsensical that so many cameras aren't supported in 8.10.

---

