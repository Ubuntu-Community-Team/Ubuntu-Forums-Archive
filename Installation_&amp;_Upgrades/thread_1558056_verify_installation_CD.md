---
title: "verify installation CD?"
date: 2010-08-21
forum: Installation &amp; Upgrades
---

### Post by garyed on 2010-08-21
In older live CD versions there was an option to check the CD integrity before installing. I didn't see anywhere on the 10.04 CD to do that.
Is there a way to test the CD integrity or if it boots up live O.K. does that mean it already passed the test?

---

### Post by dagdeniz on 2010-08-21
I don't think so. However, md5sum is a good way to check integrity. If you use linux, you can run "md5sum /dev/cdrom" and compare the output to the md5sum file on the website.

---

### Post by garyed on 2010-08-21
I think md5sum only checks the iso file.
I already did that, I want to check the integrity of the CD I burned.
Older versions of Ubuntu had an option when you booted the CD to "check CD integrity" but I didn't get one on the 10.04 live CD.

---

### Post by dagdeniz on 2010-08-21
No, it normally checks the cd, too, but if you don't try to do so, of course it doesn't. 
However if you manage to find "check integrity" in the live cd, do it that way...

---

