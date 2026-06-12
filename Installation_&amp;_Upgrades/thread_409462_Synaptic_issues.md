---
title: "Synaptic issues"
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by DaymItzJack on 2007-04-14
Everything was working fine for a week or two then I got this message:

> 
[quote]E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-multiverse.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

This is what my file looks like:

> # automatically added by gnome-app-install on 2007-04-02 23:02:00.546459
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security main universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe


I don't see any problems.

---

### Post by CompShrink on 2007-04-14
The 2nd line is missing the section you want. Note how the 3rd and 4th lines have main and/or universe listed? You need something like that, format should be:

deb URL edgy(-somethingoptional) SECTION1 (SECTION2 SECTION3)

With the stuff in () as optional.

I would suggest:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

---

### Post by DaymItzJack on 2007-04-14
Done, saved  it, opened synaptic and still errored:

> E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

This is what my file looks like now:

> # automatically added by gnome-app-install on 2007-04-02 23:02:00.546459
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security main universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe

---

### Post by zvacet on 2007-04-14
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

---

### Post by CompShrink on 2007-04-15
Hm, I just replaced my sources.list with what you put, and it works fine...

Try creating a new file, copy and paste that in, and see if that works. Maybe there's a hidden "non-printing" character in your file?

If not, sorry, I'm stumped.

---

