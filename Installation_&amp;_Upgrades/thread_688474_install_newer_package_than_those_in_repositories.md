---
title: "install newer package than those in repositories"
date: 2008-02-05
forum: Installation &amp; Upgrades
---

### Post by herchu on 2008-02-05
Hi, 

I want to install a package (kipi-plugins) which has a release newer than the one available in Ubuntu repositories. I heard that one of the ways would be to download a tarball, compile and install it -- but I don't want to install in this particular machine all the dependencies to build it (x11-dev and a lot of kde stuff I guess).

Is it there any repository from which packages can be grabbed, before they are in the official and stable repositories? I am new to ubuntu, but I have done something similar on Gentoo by adding "~x86" keyword to some selected packages, thus allowing them to be installed.

Thanks!
Hernan.

---

### Post by Odrodzona-Sarmacja on 2008-02-05
Just download .deb files and click on them. They will install automatically on your ubuntu.

---

### Post by herchu on 2008-02-06
but I have no .deb.... This product at least has only source tarballs and a few other packages for other distros.
Are there any deb repository with unstable packages for ubuntu, from which I can look for newer packages than those in the stable repos?

---

### Post by zvacet on 2008-02-06
> but I don't want to install in this particular machine all the dependencies to build it (x11-dev and a lot of kde stuff I guess).

In every way you use to install that program you will have to install dependencies,because without them program will not work.

---

### Post by bwtranch on 2008-02-06
The newest is not necessarily the best. Try installing the one from apt first. It will auto update your repos and just see if it works. You can remove it with apt if you don't like it as well.

---

### Post by louieb on 2008-02-06
Yea there are a bunch of unofficial Ubuntu repositories out there. You'll just have to Google around and see if there one that has the packages you need. Bu t heres a place to start. [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Its been my experience that come upgrade time (next one due in April when Hardy come out) that these 3rd party repositories can cause problems. (Automatix comes to mind).

---

### Post by bwtranch on 2008-02-06
Hardy's out on my machine, and so is FF 3.0

---

### Post by bwtranch on 2008-02-06
Something weird is going on here. That last post was on another one. I am going to have to call up an Administrator.

---

### Post by herchu on 2008-02-08
thanks zvacet
yes, I will need *runtime* dependencies, which I already installed. What I don't want to install, if I can avoid it, is the big list of dependencies to compile the package from source. (I was about to do it, and aborted when missing dependencies started to appear)

---

### Post by herchu on 2008-02-08
> **bwtranch said:**
> The newest is not necessarily the best. Try installing the one from apt first. It will auto update your repos and just see if it works. You can remove it with apt if you don't like it as well.

I did install the one from apt already. I was missing one feature that I found by googling that was already implemented, and that is how I ended up in that project's homepage, comparing the version in its homepage vs. the version in apt repositories.

---

