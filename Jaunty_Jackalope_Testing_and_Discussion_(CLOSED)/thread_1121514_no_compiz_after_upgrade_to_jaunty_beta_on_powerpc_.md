---
title: "no compiz after upgrade to jaunty beta on powerpc ibook"
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by oimon on 2009-04-10
hello

running on ibook powerpc g4 14 inch, 14.2ghz
graphics card is
VGA compatible controller: ATI Technologies Inc M11 NV [FireGL Mobility T2e] (rev 80)

lsmod shows the radeon driver is in use, and glxinfo tells me it is doing direct rendering. glxgears has weird colours and only 60-80 fps but i didn't try that it 8.10

8.10 was running compiz with wobbly windows.

i have just upgraded to jaunty beta and trying to enable compiz gives "desktop effects could not be enabled"

anyone else experienced this problem?

---

### Post by macinnisrr on 2009-04-12
same problem. I tried installing envy to check on my drivers but to no avail.

---

### Post by syko21 on 2009-04-12
ATI dropped support for older devices on the new Xorg. Until the open source drivers catch up to the 3D performance of the binary drivers you won't have compiz in jaunty.
Seeing as how there were not any major feature changes from intrepid to jaunty you should probably stick it out with intrepid until karmic unless there is a specific feature you need from jaunty.

---

