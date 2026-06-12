---
title: "APT-GET - Looking for mirror sources"
date: 2005-06-19
forum: Installation &amp; Upgrades
---

### Post by jemt on 2005-06-19
Hi experts.

I was wondering if there is some sort of APT-GET mirror list available somewhere ? I would really like being able to install the newest software directly from the software (stable, NOT unstable software)

Does it matter whether I use an Ubuntu og Debian sources ?

 - Thanks for all your help. Ubuntu really seems to be a great distro. I've been running Mandrake for almost 2 years now (before that Redhat starting from 5.2, then Knoppix for some years and finally Mandrake). So I can't wait to get my new linux distro running :)

---

### Post by DJ_Max on 2005-06-19
If you want to install directly from the software developers, then grab the source and compile it from there. If you want the latest, use the Ubuntu backports. Use Ubuntu sources, not any other distros sources.

---

### Post by jemt on 2005-06-19
Hmm, I'm pretty sure I have read that it is possible to use Debian sources. After all, Ubuntu is "just another" Debian clone. Besides that I'd like to know if it is possible to install RPM packages using APT-GET (and at the same time obtain dependencies if needed).

The reason why I want to find a mirror is, that I'm not too happy with the old software Ubuntu 4.10 comes with (yes, I know that a newer version has been released, but right now I'll haft to do with the "old" version). I want to update OpenOffice to the most resent version 1.4 (or maybe even 2.0 Beta) among other programs.

There is now way I'm gonna compile my programs my self. My computer is only a 866 Mhz PIII. And if I was going to compile my stuff my self, I would probably choose Gentoo over Ubuntu ;) But that's exactly what's so great about Ubuntu - all packages are pre-compiled.

---

### Post by jemt on 2005-06-19
Yeah! I just "asked" google an found this great page :
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Might come in handy to other Ubuntu users in the same situation as I was :)

---

### Post by Lunde on 2005-06-19
[http://ubuntuguide.org](http://ubuntuguide.org) is excellent. A good place to start getting some function into your box.

---

### Post by DJ_Max on 2005-06-19
[QUOTE=jemt]Hmm, I'm pretty sure I have read that it is possible to use Debian sources. After all, Ubuntu is "just another" Debian clone. Besides that I'd like to know if it is possible to install RPM packages using APT-GET (and at the same time obtain dependencies if needed)[/QUOTE]
You're gonna put yourself in some trouble. First off, do not use Debian repositories, Debian developers and Ubuntu developers package software differently. Go ahead and use Debian repositories if you want to, but be prepared for breakage. There really is no reason to use Debian repositories.

Second, RPM is meant for Red Hat based distros. Why would you wanna use  rpm's anyway. All of the up-to-date software is in the official backports. Why haven't you upgraded your distro? Makes sense if you want recent software. Use those and be happy.

---

### Post by jemt on 2005-06-19
I just thought that older versions of Ubuntu used the same sources as the newest version. So I kind of expected to be able to download the newest software, even though I'm using v. 4.1. But that's not how it works ?

---

### Post by DJ_Max on 2005-06-19
[QUOTE=jemt]I just thought that older versions of Ubuntu used the same sources as the newest version. So I kind of expected to be able to download the newest software, even though I'm using v. 4.1. But that's not how it works ?[/QUOTE]
Nope. Reason being, for example, Warty uses XFree86 X server, while Hoary uses Xorg. This is a very important, because now developers have to make binaries to build against Xorg, rather then Xfree86. Same with the GCC version, which is a crucial compiler. There are others as well.

---

### Post by jemt on 2005-06-20
Oh ok - IC. Thanks :)

I'm now running Ubunto Linux 5.04 - runs very smooth

---

