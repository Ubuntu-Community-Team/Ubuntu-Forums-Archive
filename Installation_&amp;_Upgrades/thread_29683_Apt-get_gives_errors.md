---
title: "Apt-get gives errors"
date: 2005-04-25
forum: Installation &amp; Upgrades
---

### Post by Turambar on 2005-04-25
I have just installed Ubuntu, and I have tried to install various packages with apt-get: codecs, wine... I get an error that says: "E: Couldn't find package e.g. w32codecs". I have searched this forum in order to get mp3s working, and everywhere is said that install those w32codecs and gstreamer0.8-plugins. I have done just as the HOWTOs and guides say. I have even copy-pasted the text from these pages so I can't have mispelled. Is the apt-get server down or something? This has been happening since I installed Ubuntu i.e. since Saturday. This is really annoying, almost everything works expect the mp3s.

Also where could I download these packages when the apt-get doesn't work? If it is possible, does the package depency system work?

I apologize if my English is poor.

---

### Post by andvaranaut on 2005-04-25
Hi Turambar

Check [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories) and follow the instructions. Specifically, you need to add the lines:
```
deb ftp://ftp.nerim.net/debian-marillat stable main
deb ftp://ftp.nerim.net/debian-marillat unstable main
deb ftp://ftp.nerim.net/debian-marillat testing main
```
at the end of **/etc/apt/sources.list**. Then, run **apt-get update** and all should be fine.

Hope this helps.

---

### Post by heimo on 2005-04-25
If you're using Finnish mirrors, try the Swedish (se). 

Here's my current /etc/apt/sources.list:

```
deb http://se.archive.ubuntu.com/ubuntu hoary main restricted universe multiverse
deb-src http://se.archive.ubuntu.com/ubuntu hoary main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

##deb http://se.archive.ubuntu.com/ubuntu hoary-updates main restricted
##deb-src http://se.archive.ubuntu.com/ubuntu hoary-updates main restricted

deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted

#deb ftp://ftp.nerim.net/debian-marillat stable main
deb ftp://ftp.nerim.net/debian-marillat unstable main
#deb ftp://ftp.nerim.net/debian-marillat testing main

```

And someone elso on this forum wrote these nice short instructions of using apt-get:
 > sudo apt-get update # is to update the package database
sudo apt-cache search somepackage # to search, of course
sudo apt-cache show somepackage # to see info on a package
sudo apt-get install somepackage # to install a package
sudo apt-get remove somepackage # to remove a package
sudo apt-get dist-upgrade # to upgrade the entire distro to the latest available



EDIT: To clarify why I suggest switching to *se *is because I had problems with *fi *

---

### Post by Turambar on 2005-04-25
Thanks! The right answer came very quickly.

Apt-get is working perfectly now, I used heimo's sources.list.

Updates are downloading quite slowly, I hope everything will work.

---

### Post by heimo on 2005-04-25
It's the nerim repository that's slow (at least for me it is). BTW, these couple lines  should be corrected (to get all security updates):

 ```
deb http://security.ubuntu.com/ubuntu hoary-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted universe multiverse

```

---

