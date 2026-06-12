---
title: "Installing monodevelop from source"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by Elrohir on 2007-06-06
Has anyone managed to install monodevelop from source? In repos the version is 0.12 but I have to use 0.13 for some work I got going on with Galaxium... anyone? thanks in advance!

---

### Post by Elrohir on 2007-06-06
bump

---

### Post by Immolatus on 2007-06-06
what's the problem?

---

### Post by Elrohir on 2007-06-06
let's begin then:

I managed to install mono from source, but for fulfilling monodevelop dependencies, I begin with gtk-sharp-2.4.3.tar.gz and when compiling it says mono is not installed on my system... from there we'll continue...

---

### Post by Elrohir on 2007-06-06
nobody?

---

### Post by Mr. Picklesworth on 2007-06-06
I suggest you use ```
sudo apt-get build-dep monodevelop
```
That may be all you need for 0.13, since Feisty is only one version behind. It worked for me, anyway :)

A little tip, too: If you want to use the Version Control add-in (in my opinion  the only working SVN graphical interface out there!), you'll need to run ./configure with --enable-subversion.

---

### Post by Immolatus on 2007-06-07
bingo!

---

### Post by lukew on 2007-06-07
> **Elrohir said:**
> Has anyone managed to install monodevelop from source? In repos the version is 0.12 but I have to use 0.13 for some work I got going on with Galaxium... anyone? thanks in advance!

I asked about when this would be ported into backports; though no one seems to know :(. Seems some applications get a higher priority than others.

Luke

---

