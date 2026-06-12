---
title: "How to run 32 bit apps and Opera on amd64/x86_64"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by dkuhlman on 2007-10-29
I've been searching for and reading messages about how to run the Opera Web browser on an Ubuntu amd64 installation.

Is there any more help on running 32-bit/386 applications in general and Opera in particular?

I tried to install opera by downloading the .deb from the Opera download site, then using

```
dpkg -i --force-architecture opera_9.24-20071015.6-shared-qt_en_i386.deb
```

But, when I try to run opera, I get the following error message:

```

$ opera
exec: 264: usr/lib/opera/9.24-20071015.6/opera: not found

```

Am I missing some libraries?  I notice in aptitude that there are some packages with names like ia32-libs*.  Do I need to install one of these?  Which one?

I'm running Kubuntu gutsy amd64.  It's working great.  But, I do miss Opera.

Dave

---

### Post by dkuhlman on 2007-10-30
> **dkuhlman said:**
> I've been searching for and reading messages about how to run the Opera Web browser on an Ubuntu amd64 installation.

Is there any more help on running 32-bit/386 applications in general and Opera in particular?


Some follow-up, and answering my own question.

There is now an x86_64 version of Opera.  It's a beta version.  It is Opera version 9.50b.

I've been using it for several hours now, and it seems to work great.

What I found is a snapshot.  So, by the time you read this, you should look for an even newer version.

I found it here:

```

    ftp://ftp.opera.com:/pub/opera/linux/950b/final/en/x86_64/

    opera-9.50-20071024.2-shared-qt.x86_64-1643.tar.bz2

```

Dave

---

### Post by hok on 2008-04-03
Thanks for replying to your own post dkuhlman - found it very useful

There was also a .deb file at the same location when I looked:

opera_9.50-20071024.2-shared-qt_amd64.deb

Just downloaded it, right-clicked, chose install and that was it (on gutsy studio) .  Dead easy.

---

