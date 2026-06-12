---
title: "no updates for last 2 days"
date: 2008-10-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by shuttleworthwannabe on 2008-10-29
Shame...I have terrible withdrawal symptoms...tremors, insomnia, and one hell-o-va hangover!

:popcorn:

---

### Post by ronacc on 2008-10-29
try to hold on man , JJ will be here soon :lolflag:

---

### Post by kyleabaker on 2008-10-29
I'm holding on too... \\:D/

---

### Post by kaibob on 2008-10-29
I checked for updates earlier today and got nothing, but then one showed up about 2 hours ago (just one file). This surprised me, as I assumed everything was locked down for the big rollout tomorrow.

---

### Post by kyleabaker on 2008-10-30
Yep, you're right. I checked earlier with nothing, but just got an update.

---

### Post by ad_267 on 2008-10-30
I just got an update to the base-files package. I guess they were just changing the version name from beta (or release candidate or whatever it was) to plain 8.10.

---

### Post by Kow on 2008-10-30
> **ad_267 said:**
> I just got an update to the base-files package. I guess they were just changing the version name from beta (or release candidate or whatever it was) to plain 8.10.

It was marked as a security update.

---

### Post by ad_267 on 2008-10-30
Hmm I doubt it was really a security thing. If you do a "dpkg-query -L base-files" or "apt-cache show base-files" all that package contains is the basic file system layout and files describing the distribution. I think maybe it was marked as a security update to make sure everyone got it.

---

### Post by Miguel on 2008-10-30
You could try to see the changelog via aptitude (no need to be root for this, BTW):

```

aptitude changelog base-files

```

Remember hitting "q" exits. Or you could also see the changelog directly with vim (because vim can open gzipped files on the fly):
```

vim /usr/share/doc/base-files/changelog.gz

```

Remember you need to hit ":q" to exit vim ;). I'm not using Intrepid, by the way, but Hardy got today another update from hardy-proposed and the package was... yes! base-files!. The reason was correcting some group ownership of some files in Ubiquity or so, probably for upgrading from Hardy to Intrepid.

---

### Post by forger on 2008-10-30
> **Miguel said:**
> 
Remember hitting "q" exits. Or you could also see the changelog directly with vim (because vim can open gzipped files on the fly):
```

vim /usr/share/doc/base-files/changelog.gz

```


```
cat /usr/share/doc/base-files/changelog.gz | gunzip
cat /usr/share/doc/base-files/changelog.gz | gunzip | head
cat /usr/share/doc/base-files/changelog.gz | gunzip | less
```

:KS

---

### Post by ad_267 on 2008-10-30
Oh ok that's kool. I didn't know you could do that. I was wrong, it was a security update:

> base-files (4.0.4ubuntu2.1) intrepid-security; urgency=low

  * SECURITY UPDATE: change permissions of kernels copied from the Live CD
    by Ubiquity 1.9.4 thru 1.10.9. LP: #290798.

  * Correct group ownership of files changed by Ubiquity 1.7.5 thru 1.10.9.
    LP: #288479.


---

