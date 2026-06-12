---
title: "trying to install a fedora core RPM"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by falkenberg_cph on 2007-03-28
Hi
i want to install a file called csound-java. Unfortunately it is made for SUSE. Are there any workarounds to make this work with ubuntu?

[details about the file](http://rpm.pbone.net/index.php3/stat/4/idpl/3985470/com/csound-java-5.05-0.pm.1.i586.rpm.html)

Sincerely
Carsten

[EDIT]: Sorry for themisleading title.that was because the file for fedora was 5.03, and i found the 5.05 file while writing. forgot to change the title though :D

---

### Post by spin2cool on 2007-03-28
csound and csound-java are in the universe repository - I assume these aren't what you're looking for, though.

there's a program called alien that will let you convert RPMs to DEBs, but it may or may not work.  I'd say your best bet is to find the source code and compile from source.

---

### Post by falkenberg_cph on 2007-03-28
I would prefer the newest version (i have csound 5.05 installed - csound-java would have to match).
But even if i found the source (which shouldnt be a problem, there is a link to it in the above link), and i managed to compile it, wouldnt it still need some Suse specific libraries?

/Carsten

---

### Post by falkenberg_cph on 2007-03-28
Ok. just used alien - that was easy :D
Thanks alot
Carsten

---

