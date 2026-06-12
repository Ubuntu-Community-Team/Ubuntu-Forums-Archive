---
title: "Problem with ISO packages?"
date: 2011-08-12
forum: Installation &amp; Upgrades
---

### Post by lazerking9 on 2011-08-12
Just downloaded the new (x86) iso off the Ubuntu website. I got about a third of the way through installing (Gnome, 11.04) on my desktop, when I got this error:
(paraphrasing)
```
Error during installation- could not install package 
[INDENT]FILE:///cdrom/pool/main/u/udev/libudev0_167-0ubuntu3_i386.deb
[/INDENT]package may be corrupt.
```

I verified that the specified package was actually NOT corrupt (MD5/SHA1 matched website). I even swapped in a fresh download of that file onto the CD and STILL won't work.

Anybody know what I can do?

#Note: Yes, it is is a 32-bit machine. Yes, there was enough space (120GB- the entire drive). Yes, i've done this before (with other ubuntu/debian/fedora releases). Yes, other 10.04+ releases worked fine, including 11.04STUDIO.

---

### Post by steve11911 on 2011-08-13
Hhmmm...

4 possible causes come to mind:

1.) Bad cd reader? Maybe...but not likely.
2.) Hardware futzle? Probably not since 11.04 studio works.
2.) Bad disk? As unlikely as it seems this is probably the  culprit.I would re-download the .iso, verify the md5 checksum and reburn at the lowest speed.Just to be sure I'd try the disk in another machine.
4.) Mysterious unknown hidden cause? (Bizarre quantum interference,non-locality violation,Aliens)etc...? If the new disk doesn't work we may have to take a closer look at these...

---

### Post by lazerking9 on 2011-08-14
Looked into the possibilities you said-
1) Not a problem with the drive- works fine with everything else i've tried
2) Like you said, almost probably not. I tried a bunch of the other *buntu releases, and they are all fine.
3) 99% sure it's not the disc. all the checksums match (the disc as a whole AND the individual files).
4) It wasn't aliens. No crop circles in my yard ;)

I am at a loss here. This is the first problem i've had with linux, and i've been experimenting with the different "flavors" of linux since... 2005?

---

### Post by dFlyer on 2011-08-14
Did you run a disk check on the disk after your burned it?

---

