---
title: "Is there an easy way to install codexes, I forgot to hit the checkmark during install"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by nolag on 2010-11-09
I installed ubuntu and remembered, but I told a friend to install it and forgot to mention he wanted to check that one as well.  Is there a way I can fix that without going and geting them all?

---

### Post by dino99 on 2010-11-09
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by nolag on 2010-11-09
> **dino99 said:**
> [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
 
no 10.10 on that site.

---

### Post by halj32 on 2010-11-09
run this in a terminal 
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

now you can install w32 codex etc 
or install ffmpeg

---

### Post by sikander3786 on 2010-11-11
> **nolag said:**
> no 10.10 on that site.
It is the same as for 10.04.

Simply, this command works for me and many others.

```
sudo apt-get install ubuntu-restricted-extras
```

It contains codecs, flash, java, fonts etc. All-in-one pack.

---

