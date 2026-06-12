---
title: "Update Error - Update Manager"
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by terraks on 2009-12-24
Every time that I try to update my system using Update Manager I get this error and it does not allow me to update my system:

Failed to fetch [http://download.tuxfamily.org/3v1deb/dists/feisty/Release](http://download.tuxfamily.org/3v1deb/dists/feisty/Release)  Unable to find expected entry  eyecandy/binary-lpia/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

Does anybody know what I should do to fix this and to keep my system up to date?

Thanks.

---

### Post by snowpine on 2009-12-24
You added some junk to your software sources (tuxfamily.org is not part of a standard Ubuntu install, and Feisty is an old release that's no longer supported). Why did you add this software source? Whoever gave you this bad advice should now help you solve the problem (in my opinion).

If that doesn't work, my suggestion is:

```
gksu gedit /etc/apt/sources.list
```

Find the line containing [http://download.tuxfamily.org](http://download.tuxfamily.org) and type a # symbol at the beginning of the line (to "comment it out" so that it's skipped). Then save the file and try your upgrade again.

If you've added this software source for a specific reason, you need to be clear why, so we can help you.

---

### Post by terraks on 2009-12-25
Thank you, this worked great.

I am new to the Ubuntu/Linux world. When I first got it, a few months ago, I tried to upload the fun bouncy screens for my laptop with great failure. I am guessing that while trying to following different instructions on how to do this I added the tuxfamily and/or feisty files.. without really knowing what I was doing.

Thanks again.

---

