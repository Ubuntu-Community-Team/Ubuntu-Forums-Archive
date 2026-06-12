---
title: "When will compatible ATI Catalyst be available?"
date: 2009-02-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by christian.convey on 2009-02-05
Does anyone know when ATI plans to release a proprietary driver that works with 9.04's X server?

I've got a 4850-based card that for some reason is only happy with the proprietary drivers from ATI.  (The other drivers lead to a white screen of death.)

---

### Post by Naddiseo on 2009-02-05
The open source radeon driver works will with the 4850. Just doesn't have 3d acceleration yet, so can't play movies :(, oh well, I guess that's why I have a PS3 as well.

---

### Post by MilesRdz on 2009-02-05
Hopefully now that the documentary for the newer cards is out they can build a decent open source driver.

---

### Post by Slug71 on 2009-02-05
New drivers should be coming fairly soon since KMS is on the way which needs support from the drivers too.

---

### Post by christian.convey on 2009-02-06
> **Naddiseo said:**
> The open source radeon driver works will with the 4850. Just doesn't have 3d acceleration yet, so can't play movies :(, oh well, I guess that's why I have a PS3 as well.
 
For some reason it doesn't work in my setup.  I get the white screen of death, unless I run in VESA more or unless I use the closed-source Catalyst driver.  That's why I care so much about the release date for the closed-source driver.

For now I've popped an old nVidia card into the computer, but I'd like to get back to having my Radeon HD 4850 card in my computer asap.

---

### Post by fictivetoast on 2009-02-11
Bump - I'm curious too.  Can get by without any 3d or effects for now, but it'd be nice to get compiz, gnome-do, and the works all back up and running.

---

### Post by Bablefish on 2009-02-12
They did fix a previous install bug

---

### Post by ssam on 2009-02-12
is the white screen caused by compiz starting?

i have seen this in the past with a 3650. compiz tries to start, but can't because of having no 3d acceleration. if you remove compiz then everything works fine.

the compiz wrapper script now spots that my card can't do compiz with the oss driver, and gives me working gnome with metacity.

bug link [https://launchpad.net/bugs/262529](https://launchpad.net/bugs/262529)

---

### Post by christian.convey on 2009-02-12
> **ssam said:**
> is the white screen caused by compiz starting?

i have seen this in the past with a 3650. compiz tries to start, but can't because of having no 3d acceleration. if you remove compiz then everything works fine.

the compiz wrapper script now spots that my card can't do compiz with the oss driver, and gives me working gnome with metacity.

bug link [https://launchpad.net/bugs/262529](https://launchpad.net/bugs/262529)

I don't think this is my bug, because I get the problem as the GDM login screen is first coming up.  Compiz, even if installed and active, hasn't started at that point afaik.

---

### Post by christian.convey on 2009-02-12
> **Bablefish said:**
> They did fix a previous install bug

Yeah, but I suspect something more than that is needed, since Ubuntu 9.04 has a new version of X server.

---

### Post by RaZoR1394 on 2009-02-12
With my 3200 mobility 9.1 complains about wrong Xorg version. Vesa won't work at all and ati, radeon, radeonhd has no 2d and 3d acceleration which leaves an almost unusable desktop.

---

