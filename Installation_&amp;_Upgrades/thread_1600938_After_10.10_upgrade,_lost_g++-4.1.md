---
title: "After 10.10 upgrade, lost g++-4.1"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by skywalk423 on 2010-10-19
I upgraded from 10.04 to 10.10 and everything went smoothly EXCEPT that g++-4.1 and all its dependencies were uninstalled, and now it's nowhere to be found in Synaptic Package Manager. How can I get g++-4.1 back??

ps. I know that I can download source and build it manually, but there has to be a more "Ubuntu-ish" way of doing it...

TIA

---

### Post by skywalk423 on 2010-10-20
Bump? Anyone?

---

### Post by Sub101 on 2010-10-20
Does g++ not show up?

If you got to a terminal and type

```
sudo apt-get install g++
```

it should install.

---

### Post by skywalk423 on 2010-10-20
Thanks for the reply.

That will get me g++ 4.4. I need an older version, specifically g++ 4.1, which until 10.10 was available in the default package repos. For 10.10 it looks like they removed it.

I know there is a way to get access to older versions of packages, I just have never had to do it before. Hoping someone can show me the way to do it right.

---

### Post by Sub101 on 2010-10-20
I think you can install from one of these debs.

[http://packages.debian.org/lenny/g++-4.1-multilib](http://packages.debian.org/lenny/g++-4.1-multilib)

If you go to the bottom there are the different architectures, pick yours and install.

---

### Post by tommpogg on 2010-11-02
I have got the same problem: I need g++4.1 but it has been removed from the available Ubuntu packages

> **Sub101 said:**
> I think you can install from one of these debs.

[http://packages.debian.org/lenny/g++-4.1-multilib](http://packages.debian.org/lenny/g++-4.1-multilib)

If you go to the bottom there are the different architectures, pick yours and install.

This solution could work but, if I have to manually install all the dependencies, it requires a lot of time.

Any other solution?

Thank you

---

### Post by Sub101 on 2010-11-02
> **tommpogg said:**
> I have got the same problem: I need g++4.1 but it has been removed from the available Ubuntu packages



This solution could work but, if I have to manually install all the dependencies, it requires a lot of time.

Any other solution?

Thank you

If you try it, does it not install the dependencies for you?

---

### Post by tommpogg on 2010-11-14
> **Sub101 said:**
> If you try it, does it not install the dependencies for you?

No it doesn't. It seems that g++ 4.1 and all the related packages are no longer supported.

---

### Post by tommpogg on 2010-11-17
Hi, I solved the problem by manually installing g++-4.1. This is what I have done:

1) Install texinfo (e.g. apt-get install texinfo)
2) Download gcc-4.1.2 from [http://gcc.gnu.org/](http://gcc.gnu.org/) (gcc-4.1.2 contains g++-4.1)
3) Extract it and lauch "configure"; you can use the option --prefix=GCCPATH to set the installation path.
4) Open the Makefile and modify the line 

MAKEINFO = /opt/GNUARM/newlib-1.15.0/missing makeinfo
to
MAKEINFO = makeinfo

5) launch "make"
6) launch "make install"

Notice: steps 1 and 3 are required to fix a bug in gcc-4.1.2's installation files

It is a little bit complicated but it works!

---

### Post by Smiddy12 on 2010-11-30
I agree. As a matter of fact, I installed Ubuntu for this very reason instead of my typical Arch build. It is pretty moronic that this package was removed, thanks for the instructions tommpogg.

---

