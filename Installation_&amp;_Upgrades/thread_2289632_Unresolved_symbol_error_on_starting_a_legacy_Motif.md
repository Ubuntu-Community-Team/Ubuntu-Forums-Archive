---
title: "Unresolved symbol error on starting a legacy Motif application..."
date: 2015-08-05
forum: Installation &amp; Upgrades
---

### Post by Brian_Cowan on 2015-08-05
When starting a legacy Motif 2.2 application on an Ubuntu 14.04 host, we get this little bit of fun:
symbol lookup error: [redacted path]: undefined symbol: XmRedisplayWidget

The application worked fine on Red hat Linux 6.everything. (with openmotif installed)

After a lot of digging, we found out that after installing libmotif[-common|3|4] and libmotif[-common|3|4]:i386, libXm.so.3 was actually a symlink to libXm.so.4. And a quick "strings" check confirmed that the symbol wasn't defined. On a RHEL 6.6 system, libXm.so.3 was a symlink to libXm.so.3.0.2, and contained that symbol reference.

I look in the man pages and that widget call is in the man pages that came along for the ride when I installed libmotif-dev.

What we wound up doing was grabbing an older version of libmotif3, and then manually installing it:
mkdir libmotif
cd libmotif
wget [http://hr.archive.ubuntu.com/ubuntu/pool/multiverse/o/openmotif/libmotif3_2.2.3-4_i386.deb](http://hr.archive.ubuntu.com/ubuntu/pool/multiverse/o/openmotif/libmotif3_2.2.3-4_i386.deb)
dpkg -x ./libmotif3_2.2.3-4_i386.deb  .
<copy/move appropriate libraries>

Now here is the question, the lack of a *documented* symbol in a library is a defect, but whose? Is this a Canonical packaging issue, or an openmotif issue? Essentially, "who do we yell at?" which is the biggest question when dealing with open source. Is Libmotif4 supposed to be fully backwards compatible with libmotif3? If I look at [https://motif.ics.com/motif/downloads](https://motif.ics.com/motif/downloads) I see that it claims that the "latest" is 2.3.4-1, yet apt --installed list says:
libmotif-common/trusty,now 2.3.4-5 all [installed]
libmotif3/trusty,now 2.3.4-5 amd64
libmotif4/trusty,now 2.3.4-5 amd64

Incidentally, the XmRedisplayWidget symbol *is* in the 2.3.4-1 download from [https://motif.ics.com/motif/downloads](https://motif.ics.com/motif/downloads). But finding the source/changelog for the -5 version seems to be a challenge. So, we wind up with the same question... is -5 a Canonical thing or an Integrated Computer Solutions thing?

---

### Post by tgalati4 on 2015-08-06
Well, Motif is an old widget set.  I remember using it in the early 1980's.  Your situation demonstrates the different packaging methods between Red Hat and Debian-based Linux operating systems.

For your questions:  There is no *openmotif* package for Ubuntu, so that is a dead end.  I suppose you could convert it using *alien*--which would attempt to convert the *openmotif* package from Red Hat to Ubuntu.  This is not always successful, and generally not recommended because of system breakage that could occur.

You could simply file a bug against *libmotif* and let the bug tracking system kick it around a few times.  Reference this thread and mention your work-around.  I don't know if there is a Motif-to-newer-widget-set (perhaps gnome2) script that you could run the application through.  

As the frameworks that make up Linux are constantly changing such breakage is bound to happen.

---

### Post by Brian_Cowan on 2015-08-06
Well, if you could point me to where to enter the bug... The MotifZone.org bug tracker doesn't exist anymore, so would I be looking at an upstream (debian) bug, or a canonical one?

---

### Post by Brian_Cowan on 2015-08-06
Ah, no LMGTFY links please... I filed it against debian: [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=794786](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=794786)

---

### Post by Brian_Cowan on 2015-08-06
In case anyone else sees this, this is apparently because support for  the (deprecated) X Print API was removed as per Debian "bug" 657253.  Given the extreme age of the application, and the API, and that the API  was officially deprecated about 8 years ago... Well, looks like we are  done here. The Debian maintainer said that this was the first program  he's seen that used X Print... And we don't use it for "printing"...

---

### Post by tgalati4 on 2015-08-07
Well old is old.  Really old is really old.  Sounds like your application is really old.  Perhaps you can run the application on a Red Hat 6 virtual machine which is hosted by Ubuntu 14.04.

---

