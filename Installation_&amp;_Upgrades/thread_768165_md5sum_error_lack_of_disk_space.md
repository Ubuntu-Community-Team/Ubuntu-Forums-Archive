---
title: "md5sum error lack of disk space?"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by jingo811 on 2008-04-26
I have downloaded a 4.1 GB OpenSuSE DVD iso.
/ has 2.3 GB available.
/home has 4.7 GB available. 

```
$ md5sum openSUSE-10.3-GM-DVD-i386.iso 
md5sum: openSUSE-10.3-GM-DVD-i386.iso: Input/output error
```

Is this error caused by a corrupt download or do I have to little disk space on / and /home in order to do a complete md5sum on this 4.1 GB iso file?

---

### Post by kidders on 2008-04-27
Hi there,

I'd go with the second one ... even if your download *was* corrupt, md5sum would have no trouble reading it. It'd just spit out a different hash than the one you're expecting. "Input/output error" could also indicate physical problems (eg damage to the surface of your hard disk), but I don't suppose that's likely.

In theory, if you were to skip the md5sum check, you'd be exposing yourself to...[LIST]
[*]the risk of installing an OS that's been tampered with, or
[*]winding up with missing or damaged files on your new install, or
[*]encountering errors part of the way through the installation process, or
[*]burning a disc that fails to boot.
[/LIST]

These aren't risks worth taking on production systems, but if your box is for personal use, burning the ISO to disc & crossing your fingers might just be faster/easier than freeing up the necessary disk space. It's up to you.

---

