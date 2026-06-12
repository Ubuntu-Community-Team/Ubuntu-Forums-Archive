---
title: "problem in reinstalling adobe flash after crashing"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by chyu on 2010-08-12
hi everyone,

After I followed some instruction got from some website to make DVD and music play well, I found that adobe flasher was crashed .
So that , I tried to reinstalled but failed as computer said "another synaptic running in non interactive mood. please wait for it to finish it."
I don't know what synaptic has been running and still not yet finished .
Could you please give me some idea for my problem ?
what I know about computer is not much and could you explain in simple way?

I really appreciate your help.

---

### Post by earthpigg on 2010-08-12
click/look around your desktop, see if the update manager is trying to tell you something.

---

### Post by chyu on 2010-08-14
I tried again to reinstall adobe flash plug in and adobe flash player and I think I made it.
However, I can't play dvd on computer (I use movie player which  used to play dvd and cd on computer) as error occured " Could not open location; you might not have permission to open the file".
Could you please give me some idea about this?
Thank you,

---

### Post by earthpigg on 2010-08-14
from the [ubuntu wiki]("https://help.ubuntu.com/community/RestrictedFormats"):

> To play DVDs, you also need to install libdvdcss by opening a terminal and entering the following in addition to installing the restricted extras package:

 ```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

what method did you use?

---

