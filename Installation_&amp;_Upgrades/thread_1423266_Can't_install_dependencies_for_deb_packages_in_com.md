---
title: "Can't install dependencies for deb packages in command line system"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by PARO on 2010-03-06
I did a base command line install of Ubuntu without internet connection.  the commands apt-get install and dpkg -i would NOT install dependencies of my packages (they said they couldn't, but i know they wern't trying their hardest). aptitude install on the other hand would. I can remember using apt-get and having no problems last time around (couple years ago). But my problem is dpkg still wouldn't (and btw these were ubuntu packages downloaded in advance online because there was no internet set up). I ended up hooking the computer up to the net and aptituding the same files i had just downloaded online so that the dependencies would finally also be installed. Why is this happening, this was sooo much easier in previous versions. And is there something i'm missing in regards to dependencies with the debian packages?

---

### Post by khelben1979 on 2010-03-06
> **PARO said:**
> And is there something i'm missing in regards to dependencies with the debian packages?

Are you mixing Ubuntu and Debian packages?

---

### Post by PARO on 2010-03-06
Yeah, but the debian packages were the same versions, or well required the same version dependencies available in the ubuntu repos. I was apt-getting from the alternate cd, and dpkging the deb packages I downloaded mainly from packages .ubuntu .org (stuff that wasn't included on the cd, but would be available with an internet connection) Funny thing is after having to hook up the net and use aptitude, I started X and apt-get installs worked fine again from the terminal.

---

