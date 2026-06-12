---
title: "What's differences between apt-get and aptitude ?"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by Physicist on 2007-05-17
What is the difference between
```

sudo aptitude install sun-java6-jdk sun-java6-javadb glassfish netbeans5.5

```

and

```

sudo apt-get install sun-java6-jdk sun-java6-javadb glassfish netbeans5.5

```

Will they both install those packages?

WIll they result in the same effect?

---

### Post by aysiu on 2007-05-17
Yup. Same net effect.

---

### Post by sonofusion82 on 2007-05-18
yes.. for installing, it is mostly the same.
for older version of ubuntu (6.06 or earlier), the main difference is when uninstalling packages.
aptitude will also remove unused dependencies while apt-get will only install the particular package.
[http://www.psychocats.net/ubuntu/aptitude]("http://www.psychocats.net/ubuntu/aptitude")

---

### Post by aysiu on 2007-05-18
> **sonofusion82 said:**
> yes.. for installing, it is mostly the same.
for older version of ubuntu (6.06 or earlier), the main difference is when uninstalling packages.
aptitude will also remove unused dependencies while apt-get will only install the particular package.
[http://www.psychocats.net/ubuntu/aptitude]("http://www.psychocats.net/ubuntu/aptitude")
Well, that's changed since Edgy Eft, actually. *apt-get* now has a new feature called *autoremove* that will remove unused dependencies.

---

### Post by bukwirm on 2007-05-18
Of course, aptitude also provides an ncurses frontend if you just run "sudo aptitude".

---

### Post by Physicist on 2007-05-21
Is one of them preferred for any reason?

---

### Post by aysiu on 2007-05-21
> **Physicist said:**
> Is one of them preferred for any reason?
Well, what I do now is pretty much always use *apt-get*.

**But** if there's some kind of weird dependency conflict problem, I'll use *aptitude* to try to resolve it in a smart way.

---

### Post by ThinkBuntu on 2007-05-21
Debian recommends using aptitude for better dependency support. Today I noticed something odd though...I installed digiKam with aptitude, and it proceeded to install a bunch of KDE junk that in no way could be considered a dependency. I mean it added Konqueror, KMail, and other apps. I tested my hypothesis by removing KMail via synaptic, and sure enough, the next time I aptituded something, it uninstalled a good 75% of the junk it had added before. Granted, I needed Konqueror for browser testing, being a web designer, but this struck me as odd.

In any case, Aptitude has always been great for me in the past. It's very good at removing unnecessary apps once you've removed something.

---

### Post by spiffytech on 2007-05-22
Aptitude installs whatever you requested, but also any recommended packages, which apt-get doesn't do by default (ThinkBuntu, this may be your problem). Depending on the situation, I use either,

---

### Post by supine on 2007-05-24
> **spiffytech said:**
> Aptitude installs whatever you requested, but also any recommended packages, which apt-get doesn't do by default (ThinkBuntu, this may be your problem). Depending on the situation, I use either,

not quite true. they both install dependencies but only aptitude has the '--with-recommends' command line switch.

---

