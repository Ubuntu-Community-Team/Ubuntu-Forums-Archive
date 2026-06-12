---
title: "Can you run php4 with hardy, definitive answer?"
date: 2008-07-27
forum: Installation &amp; Upgrades
---

### Post by dimbutnice on 2008-07-27
I am *very* new to this Linux thingy, but it seems like fun, except I have to install Apache with php4 for a developer to install their application on and I can't for the life of me figure out how. PHP5 was a breeze when I tried that, but apparantly means the developer has to re-write his code which isn't an option (see told you I was new to this). I have done all the suggestions I could Google and it seems that either I don't have the right depository or it plain can't be done with this distro. If for instance I try

```
sudo apt-get install libapache2-mod-php4 php4-cli php4-common php4-cgi
```

I get an error

```
Package libapache2-mod-php4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
```

If anyone can explain what I am doing wrong in words of few syllables I would be seriously grateful.

---

### Post by scragar on 2008-07-27
have you enabled backports in the software sources option?
System>Administration>Software Sources

---

### Post by dimbutnice on 2008-07-27
> **scragar said:**
> have you enabled backports in the software sources option?
System>Administration>Software Sources

 deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
 deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

are uncommented in the sources.list file if that's the same?

---

### Post by scragar on 2008-07-27
yeah, so backports are enabled...

[http://ohioloco.ubuntuforums.org/showpost.php?p=5044700&postcount=2](http://ohioloco.ubuntuforums.org/showpost.php?p=5044700&postcount=2) <-- found that guide, not as easy as synaptic, but it's worked for other people.


php4 was dropped from hardy because PHP has been dropped by PHP, consider upgrading to PHP5 if you can, otherwise your looking for trouble later.

---

### Post by dimbutnice on 2008-07-27
> **scragar said:**
> yeah, so backports are enabled...

[http://ohioloco.ubuntuforums.org/showpost.php?p=5044700&postcount=2](http://ohioloco.ubuntuforums.org/showpost.php?p=5044700&postcount=2) <-- found that guide, not as easy as synaptic, but it's worked for other people.


php4 was dropped from hardy because PHP has been dropped by PHP, consider upgrading to PHP5 if you can, otherwise your looking for trouble later.

Yup, I saw that post, but so far as I can see it was running php4 effectively as a cgi-script. I don't know if that's a problem, I guess I'll have to get back to the developer on that. Personally I have nothing against running php5, but then I don't have to port the application over! Thanks for your time though, any other thoughts would be appreciated and I'll post back if it seems that route will work.

---

