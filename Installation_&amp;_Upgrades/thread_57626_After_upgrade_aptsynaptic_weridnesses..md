---
title: "After upgrade: apt/synaptic weridnesses."
date: 2005-08-17
forum: Installation &amp; Upgrades
---

### Post by regebro on 2005-08-17
Yesterday I upgraded from Warty to Hoary. All seems fine, except for some weirdness:

1. I can no longer change my repositories from Synaptic. Every time I try that., it instead reloads the package list! The same thing happens if I try to open the filters dialog. This is completely independent of how sources.list looks, btw, I tried an empty one, (and deleting it., which makes synaptic complain, of course).
 ](*,)  ](*,)  ](*,) 

2. I tried adding backports (by the editing the sources.list directly). I've tried with all the mirrors, and I've tried the syntaxes people have given as examples here just to make sure, but apt-get skips them with an "Ign" flag, and Synaptic claimes that some file doesn't exist.

For example, this line:
deb [http://ftp2.caliu.info/backports](http://ftp2.caliu.info/backports) hoary-extras restricted

Makes synaptic say:
W: Couldn't stat source package list [http://ftp2.caliu.info](http://ftp2.caliu.info) hoary-extras/restricted Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
 ](*,) 

As mentioned it's an upgraded Hoary, everything is latest versions as of right now.

---

### Post by zAo on 2005-08-17
Delete the backport entry and add (directly)
```
eb http://ubuntu-backports.mirrormax.net/ hoary-backports main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main restricted universe multiverse
``` 
After that run
```
sudo apt-get update
```

---

### Post by regebro on 2005-08-17
OK, that solved problem 2, thanks.

If anybody have any hints on problem 1, that would be cool, but it's no panic, this at least makes JRE pop up in the list which is what I need right now. ;)

---

### Post by regebro on 2005-09-05
Evidently nobody else than me has this problem.  :-/

---

