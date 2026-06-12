---
title: "upgrading without internet"
date: 2005-03-17
forum: Installation &amp; Upgrades
---

### Post by DFreeze on 2005-03-17
I'm planning on installing ubuntu on 2 systems. One is my mums old PC and my own is gonna be ubuntufied as well.

My mums computer does not have internet, but I do have to add some features to the basic install (like get drivers for a modem  :) ). How can I apt-get packages and dependencies on my system (which is identical to hers in the beginning), but not install them on mine, rather copy them to a CD I can then use to install from on her PC.

So the question is: where does apt-get put the downloaded files? Can I get access to them and put them on a CD? 

Thanx in advance for thinking with me!

---

### Post by Juergen on 2005-03-17
The packages are in /var/cache/apt/archives

You can install them via dpkg -i, but better IMHO is to run
```
dpkg-scanpackages ./ /dev/null | gzip > Packages.gz
```in the package-dir (or somewhere else, to have the packages in a subdir, if you want). 
After that you can add this dir (or, after burning, the cd) as repository in sources.lst and use it with apt-get or synaptic.

---

### Post by DFreeze on 2005-03-18
Thanks for your insight  :D 

So apt-get 'sees' the packages because of the listing in packages.gz. Without this file, apt-get would not see the software on the CD? 

I think I got the code part, but could you kinda walk me through it? What does scanpackages do? and what's the rest of the code for (I know gzip, but I'm a bit in the dark about the ./ etc. part)?

Excuse me for being illiterate in this field. I'm working on understanding it, hence the questions.

---

### Post by Juergen on 2005-03-18
There's always 'man' for your help...

You might want to read this:
[http://www.debian.org/doc/manuals/repository-howto/repository-howto.html](http://www.debian.org/doc/manuals/repository-howto/repository-howto.html)
dpkg-scanpackages is covered in 'Creating the Index Files'

---

### Post by DFreeze on 2005-03-18
Thanx, could've thought of that myself  ](*,)

---

