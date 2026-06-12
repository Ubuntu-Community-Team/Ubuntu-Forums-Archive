---
title: "Duplicate Ubuntu setup on different machine"
date: 2007-08-19
forum: Installation &amp; Upgrades
---

### Post by rfurman24 on 2007-08-19
I have searched and did not see anything to answer my specific question. Is there a way to duplicate my Ubuntu setup on a newly built machine with completely different hardware. I know I can copy my home directory over but what about all the installed apps?

---

### Post by Pumalite on 2007-08-19
You might want to try AptOnCD: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by rfurman24 on 2007-08-19
Looks pretty cool but as far as I can tell it only does downloaded packages not packages installed through repository. I might as well just reinstall through synaptic which is what I am trying to avoid. Thanks for the help though.

---

### Post by j_dog on 2007-08-19
It makes a cd or dvd with all the packages / applications downloaded via apt-get,aptitude and synaptic.

---

### Post by rfurman24 on 2007-08-19
I must be doing something wrong then because It is not bringing up anywhere near all my apps.

---

### Post by Pumalite on 2007-08-19
Read carefully the Documentation.

[http://linuxhelp.blogspot.com/2006/11/aptoncd-create-backup-of-all-packages.html](http://linuxhelp.blogspot.com/2006/11/aptoncd-create-backup-of-all-packages.html)

---

### Post by rfurman24 on 2007-08-19
Ya. I had read that. It does not have even close to all my installed apps. I physically looked in /var... and they are not there. Where else would synaptic keep them?

---

### Post by Pumalite on 2007-08-19
/var/cache/apt/archives

---

### Post by rfurman24 on 2007-08-20
Yep./var/cache/apt/archives Very few debs in there. 67 to be exact I should probably have in the 300's I would guess with all the dependencies.

---

