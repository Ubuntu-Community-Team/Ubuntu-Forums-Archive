---
title: "switch from debian etch to ubtuntu gutsy 7.10"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by mveltre on 2007-10-22
hi,

on a server i'm running a debian etch with some standard software like apache and mysql. But i would like to use some software available in ubuntu and also the newer kernel...

Therefore the simple question... **is it possible to just copy the /etc/apt/sources.list of an ubuntu gutsy to this server and run apt-get update && apt-get dist-upgrade ? ;-) **Without destroying ...

(and would this still work if I use loop-aes encryption on some data-devices)

Thanks,
Markus


PS: reason: no physical access to the server (running i a NOC)

---

### Post by kerry_s on 2007-10-22
dude in debian you just add the other repos for lenny and sid. ubuntu is just a snapshot of debian sid:

example:

```


deb http://ftp.debian.org/debian/ etch main contrib non-free 
deb http://ftp.debian.org/debian/ lenny main contrib non-free 
deb http://ftp.debian.org/debian/ sid main contrib non-free 


```

also debian and ubuntu are different distro's, there's alot of compatibility loss.
also just to let you know if your going to upgrade all the way up to sid, you need to do testing/lenny first, then add the sid/unstable and upgrade the rest of the way. other wise you'll get a not enough cache error.

i recommend you just stop at lenny, it has the same kernel as in sid and is alot less risky, but if your 1 of those that always wants the newest sid will get you there.

---

