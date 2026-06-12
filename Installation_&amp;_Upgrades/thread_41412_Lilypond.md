---
title: "Lilypond"
date: 2005-06-13
forum: Installation &amp; Upgrades
---

### Post by dansoper on 2005-06-13
Hi,

I am new to Ubuntu, and so far am very impressed. As a musician I want to use Lilypond, so I managed to get that through Synaptic. However, the version is 2.2.6, and the current stable is 2.4.6.

I tried to upgrade to that by adding the Debian Sid repository, which does contain it, and it seemed to install, but would not fully run, coming up with the error

"Interpreting Music: Segmentation Fault"

Has anyone seen this, and is there a fix? I really want to use the later version of Lilypond, as its syntax is better, and the printouts cleaner.

Thanks,

Dan

---

### Post by tread on 2005-06-13
Well, there are two options as I see it.
1. Get the source and compile it yourself (you can always ask for help if you get stuck :))
2. Request the backports team to make a deb for you.

Edited to add: using deb repos can unfortunately mess things up .. ubuntu moves too fast for deb and the bad sideeffect (in my opinion) is incompatibility with debian.

---

### Post by mingus on 2005-06-13
Hello Dan,

As an aside, fyi using the Debian repositories has been strongly discouraged due to compatibility issues . . .

---

### Post by ubuntu_demon on 2005-06-13
[QUOTE=mingus]Hello Dan,

As an aside, fyi using the Debian repositories has been strongly discouraged due to compatibility issues . . .[/QUOTE]
 indeed!

If you want more/newer stuff .. add backports see :

[http://www.ubuntuguide.org/#repositories](http://www.ubuntuguide.org/#repositories)

If you can't find your package ask them (if the package is in breezy or debian and it's easy to backport they'll do it) see :

[http://ubuntuforums.org/forumdisplay.php?f=47](http://ubuntuforums.org/forumdisplay.php?f=47)

---

### Post by dansoper on 2005-06-13
Thanks for the help.  I have changed my repositories, but still the older version is the only one.  I have therefore added a request to the Backports forum.

Thanks,

Dan

---

### Post by ubuntu_demon on 2005-06-13
[QUOTE=dansoper]Thanks for the help.  I have changed my repositories, but still the older version is the only one.  I have therefore added a request to the Backports forum.

Thanks,

Dan[/QUOTE]
 welcome to ubuntu and welcome to the forums :)

---

