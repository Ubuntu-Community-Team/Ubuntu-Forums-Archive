---
title: "'packages have been kept back'??"
date: 2006-08-05
forum: Installation &amp; Upgrades
---

### Post by kaplis on 2006-08-05
hey!

 i was making update and the 3 packages dont want to install. 

root@ubuntu:/home/oskars# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade...Done
The following packages have been kept back:
  avifile-win32-plugin libopenal0 mailutils
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

what does it mean- packages have been kept back?

---

### Post by Titus A Duxass on 2006-08-05
Run the same command but with aptitude instead of apt-get, that should give you more of an explanation.

---

### Post by kaplis on 2006-08-05
i did it with aptitude. it gave the same information but with-

Need to get 0B of archives. After unpacking 0B will be used.

so it means, that such a packages doesnt exist?:confused:

---

### Post by Titus A Duxass on 2006-08-05
If you need those packages, search and see how they are available.
If everything appears to be working ignore them.

You could try aptitude dist-upgrade, that may catch those packages.

---

### Post by kaplis on 2006-08-05
ok! i will continue to fight with it:D 
tnx anyway;)

---

### Post by confused57 on 2006-08-05
I had a problem with xubuntu-desktop being "held back", it's been awhile, but I believe I resolved the issue in Synaptic Package Manager.  You could "reload", "mark upgrades", "apply" & see if this corrects it.  If not, do a search for the items in SPM & see if there is an updated version, SPM may be able to resolve any dependencies.
As I mentioned, it's been several months ago and I don't remember exactly how I did it.  You may need to enable universe & multiverse repositories, if you haven't already.

---

