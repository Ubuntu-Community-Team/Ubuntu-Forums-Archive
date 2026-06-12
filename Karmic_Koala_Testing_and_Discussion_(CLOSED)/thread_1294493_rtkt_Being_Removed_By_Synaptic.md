---
title: "rtkt Being Removed By Synaptic"
date: 2009-10-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by popejeremy on 2009-10-18
Hi. I just ran a Synaptic *Mark All Upgrades* and it has marked the package, rtkit, for removal. How can I know if rtkit is being replaced by something better, or is simply no longer necessary? I don't want to do a bad partial upgrade.

Thanks!

---

### Post by 23meg on 2009-10-18
Read the changelog ("Package > Download Changelog" in Synaptic).

---

### Post by tekstr1der on 2009-10-18
Was previously added to main. Having problems with pulseaudio so not ready for prime time yet.

```
pulseaudio (1:0.9.19-0ubuntu3) karmic; urgency=low

  [ Tony Espy ]
  * debian/control: Add a Conflicts for rtkit so we force removal, and
    hence get more testing coverage between now and Karmic final (LP: #452458).


```

also see this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/406702](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/406702)

---

### Post by popejeremy on 2009-10-18
I can't find the changelog. So what does all this stuff mean? Should I run the upgrade and remove it or no?

---

### Post by tekstr1der on 2009-10-18
Yes, you can remove it. Unless you have a particular need for it, in which case you cannot have both rtkit and pulse installed at the same time.

---

### Post by MadMan2k on 2009-10-18
> **tekstr1der said:**
> Yes, you can remove it. Unless you have a particular need for it, in which case you cannot have both rtkit and pulse installed at the same time.
even if you have a need for it, you can not use it with the current kernel in karmic. (thats why it is being removed)

---

### Post by kansasnoob on 2009-10-18
After reading this I just decided to go for it and ran apt-get dist-upgrade (hey, I haven't had any serious breakage in several days and I'm getting bored anyway), and it went off without a hitch.

Reboots without a problem, sound works (still no VIA toggles for tweaking sound however) and all seems totally functional. Well, can't comment on open office because I use abiword!

Thanks to all for parsing this update!

---

### Post by hanzomon4 on 2009-10-18
Always read the change logs... will save you problems.

---

### Post by popejeremy on 2009-10-18
> **hanzomon4 said:**
> Always read the change logs... will save you problems.

This is the second time I've seen this tip, but I don't know where to find them!

---

### Post by 23meg on 2009-10-18
> **popejeremy said:**
> This is the second time I've seen this tip, but I don't know where to find them!

Did you read the first reply?

---

### Post by hanzomon4 on 2009-10-18
The update-manager, it usually shows what changes are being made to a package... sometimes it says "the list of changes is not available yet" it which case it provides a url(in blue) to the change log

---

### Post by todak on 2009-10-18
Per the changelog: > * debian/control: Drop rtkit from recommends, as the kernel patches have
    not landed in karmic, so rtkit is currently useless.

 -- Luke Yelavich <themuso@ubuntu.com>  Wed, 14 Oct 2009 12:02:50 +1100

---

### Post by lean on 2009-10-19
Also se this:
[http://0pointer.de/blog/projects/pa-in-ubuntu.html](http://0pointer.de/blog/projects/pa-in-ubuntu.html)

---

