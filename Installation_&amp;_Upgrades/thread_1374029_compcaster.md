---
title: "compcaster"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by ricky rodgers on 2010-01-06
I have for two days now tired to install compcaster on my ubunta 9.10 pc
I have looked at tutorials etc but it wont show up???
it said it is installed but i cant find it in the programs please help
Richard.

---

### Post by dstew on 2010-01-06
What is compcaster? Do you have a link for it?

---

### Post by ricky rodgers on 2010-01-06
it is a streeming software
 
link is  [http://www.campware.org/en/camp/campcaster_news/](http://www.campware.org/en/camp/campcaster_news/)
 
richard

---

### Post by dstew on 2010-01-06
So it is **camp**caster. Did you install the debian packages, or compile from source?

Anyway, if it is installed, there should be a web-based interface, if you configured the external services as described in the /doc/installUbuntu.html document. Try putting this URL in your browser: [http://localhost/campcaster](http://localhost/campcaster). Or, on the command line:```
/opt/campcaster/bin/campcaster-scheduler.sh start
```

---

### Post by ricky rodgers on 2010-01-06
hi dstew I am very new to ubunta this is my first download lol
what i did was I used synaptic package manager
I downloaded compcaster-libs_1.40-3be 1.7 Mb
in package manager I have
campcaster-libs 1.4 0-3 beta3 and the square is green
but still not to be seen on the PC.:(

---

### Post by dstew on 2010-01-06
You have to install the other package -- [http://sourceforge.net/projects/campcaster/files/campcaster/1.4.0-beta3/campcaster-1.4.0.tar.bz2/download](http://sourceforge.net/projects/campcaster/files/campcaster/1.4.0-beta3/campcaster-1.4.0.tar.bz2/download) or if you prefer the Debian packages listed next to this tar.bz2 on the [Campcaster download page.]("http://sourceforge.net/projects/campcaster/files/")

I am not clear on how you did this with Synaptic -- I did not find Campcaster in a search of the repositories. Did you add a special repository first?

Anyway, in addition to the library package, it looks to me like you need to install the studio and station packages too.

---

### Post by ricky rodgers on 2010-01-07
ok i have downloded the  [http://sourceforge.net/projects/camp...r.bz2/download]("http://sourceforge.net/projects/campcaster/files/campcaster/1.4.0-beta3/campcaster-1.4.0.tar.bz2/download")
it is in a box do i extract it or open it  sorry i am still lerning ubuntu
richard

---

### Post by ricky rodgers on 2010-01-07
ok i give up back to windows for me ta ta ubuntu

---

