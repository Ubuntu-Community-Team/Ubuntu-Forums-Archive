---
title: "installing some eeebuntu versions on a eeepc with windows 7"
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by eeeBenny on 2009-12-25
hey there

i want to install some eeebuntu os'es in addition to my existing windows 7!

anyone can tell me how?

thx

---

### Post by raymondh on 2009-12-25
> **eeeBenny said:**
> hey there

i want to install some eeebuntu os'es in addition to my existing windows 7!

anyone can tell me how?

thx

1.  Defrag windows (2x if you have the time)
2.  back-up your files (and test it too)

You have many ways once you boot into the install liveCD:

-  You can select side-by-side (if supported.  With your mouse, grab the slider and allocate partition sizes between OS'.  Otherwise, you will have the 2.5gb install which will not be enough for the first update.

-  You can use windows disk management utility and shrink the windows partition to create space for linux.  Leave that space UNALLOCATED.  Then, boot into the installer and select "use continuous free space" which will install the OS in the previously created space.

-  You can also choose advanced install ... creating the partitions beforehand and manually installing unto them .... also separating /home from root (/).

Google around.  There are lots of tutorials on 'installing eeebuntu dual-boot windows 7".

Happy holidays.

---

