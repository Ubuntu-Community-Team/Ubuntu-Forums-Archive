---
title: "Problem updating libquicktime1"
date: 2008-09-23
forum: Installation &amp; Upgrades
---

### Post by Scotus on 2008-09-23
Hello, I'm fairly new to the Ubuntu forums.  Today I had a rather annoying little problem and I can't seem to figure out a workaround.  During the normal update installation procedure, I was prompted to update libquicktime1.  For some reason it conflicts with the older libquicktime0 package and I get an error as follows: "E: /var/cache/apt/archives/libquicktime1_2%3a1.0.2+akirad-2_amd64.deb: trying to overwrite `/usr/lib/libquicktime.so.0.0.0', which is also in package libquicktime0"

Is there any way to work around this problem??

Thanks.

---

### Post by akir4d on 2008-09-23
Please, can you say me your version of ubuntu....

byez

Paolo Rampino aka Akiard

---

### Post by Scotus on 2008-09-28
8.04 LTS (hardy heron)

---

### Post by Scotus on 2008-09-28
I forgot to mention it's the 64-bit version thanks... I understand you're the person who maintains the repository for cinelerra actually... thanks very much for that!  I believe this is a small problem... but I can't get around it.

---

### Post by akir4d on 2008-09-29
libquicktime0 not exist on regular ubuntu, check your package sources

and anyway do 
sudo apt-get remove libquicktime0

---

### Post by Scotus on 2008-09-29
It didn't work. I got the following:

The following packages have unmet dependencies:
  libquicktime-dev: Depends: libquicktime1 (= 2:1.0.2+akirad-2) but 2:1.0.0+debian-5 is to be installed

---

### Post by Scotus on 2008-10-12
Am I to take it there is no solution to this problem then?

---

