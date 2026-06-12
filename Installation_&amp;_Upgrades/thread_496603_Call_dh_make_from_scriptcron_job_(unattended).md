---
title: "Call dh_make from script/cron job (unattended)"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by h.aling on 2007-07-09
Dear forum,

I'd like to automate my building process for some application I download from SVN.

Basically, I build my packages using:
```
$ dpkg-depcheck -d ./configure
$ dh_make -s -c gpl --createorig
$ debuild -uc -us
```

But dh_make asks for an "<enter> to confirm", so I can't call it from a unattended script or cron job.

How can I bypass this behavior?

-tnx-


Harold.

---

### Post by ncarter on 2008-01-04
A bit of a hack but I ended up doing this
echo \n > newline.txt
dh_make -n -s < newline.txt

Would be nice if by default it didn't prompt or there was a switch to turn the prompting off.....

---

