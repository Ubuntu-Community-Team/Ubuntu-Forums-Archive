---
title: "Updating question"
date: 2009-09-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by zoomy942 on 2009-09-21
Everytime i have updated through the terminal, i get this at the end.  should i be concerned?

```
Processing triggers for python-support ...
WARNING: WARNING: /usr/share/pyshared/lsb_release.py is linked but does not belong to any package.
zimmerman@Karmic-Tablet:~$ 

```

---

### Post by ranch hand on 2009-09-21
Just remove the file.

---

### Post by Favux on 2009-09-24
Hi zoomy942,

Hmmm.  Some links:

bug report:  [https://bugs.launchpad.net/ubuntu/+source/lsb/+bug/418017](https://bugs.launchpad.net/ubuntu/+source/lsb/+bug/418017)

some definitions/manuals:

[http://refspecs.freestandards.org/LSB_3.1.0/LSB-Core-generic/LSB-Core-generic/lsbrelease.html](http://refspecs.freestandards.org/LSB_3.1.0/LSB-Core-generic/LSB-Core-generic/lsbrelease.html)

[http://linux.die.net/man/1/lsb_release](http://linux.die.net/man/1/lsb_release)


I'm not sure if this python "problem" is what's breaking Magick (written in python gtk) for you but this worries me a little:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=524985](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=524985)

---

### Post by zoomy942 on 2009-09-24
> **ranch hand said:**
> Just remove the file.

and how do i do that?  theres lots of them.

---

### Post by VMC on 2009-09-25
> **zoomy942 said:**
> and how do i do that?  theres lots of them.

There's only one "/usr/share/pyshared/lsb_release.py" file.

Here's the [LP]("https://bugs.launchpad.net/ubuntu/+source/lsb/+bug/418017") on the subject.

---

