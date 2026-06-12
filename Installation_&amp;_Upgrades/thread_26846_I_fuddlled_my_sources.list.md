---
title: "I fuddlled my sources.list"
date: 2005-04-14
forum: Installation &amp; Upgrades
---

### Post by RaverDK on 2005-04-14
Hey Ubuntu forum!

I have a bad taste in my mouth - i kind of forgot to backup my sources.list before screwing around in it... 


coud anyone pase a sources.list for the version 5.XX of Ubuntu...

---

### Post by Dracontopes on 2005-04-14
Here is mine:

```

deb http://archive.ubuntu.com/ubuntu/ hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hoary universe
deb-src http://archive.ubuntu.com/ubuntu/ hoary universe

deb http://security.ubuntu.com/ubuntu/ hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ hoary-security main restricted

deb http://archive.ubuntu.com/ubuntu/ hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hoary multiverse

deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted

```

---

### Post by RaverDK on 2005-04-14
Thanks! looks like it works like a charm! :)

Nice to se the Ubuntu forum is working just as good as Ubuntu as a Operation system :-)

---

### Post by Dracontopes on 2005-04-14
[QUOTE=RaverDK]Thanks! looks like it works like a charm! :)

Nice to se the Ubuntu forum is working just as good as Ubuntu as a Operation system :-)[/QUOTE]
 :) No problem!

Humanity to others...

---

