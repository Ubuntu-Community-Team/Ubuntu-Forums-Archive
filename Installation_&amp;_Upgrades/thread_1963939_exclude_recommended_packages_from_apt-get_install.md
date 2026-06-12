---
title: "exclude recommended packages from apt-get install"
date: 2012-04-23
forum: Installation &amp; Upgrades
---

### Post by oscarbenjamin on 2012-04-23
I'd like to know if there is a way, to instruct apt-get that I don't want to install recommended dependencies, either by excluding specific packages or in general. I have a script in dropbox that uses apt-get to install a large body of software that I want on any of my ubuntu systems. I would like this script to avoid installing some larger packages that I know I don't want, because in some cases for example my netbook, I have very limited diskspace.

For example, I typically install texlive-latex-extra in any ubuntu system that I use. Weighing in at around 25MB, I can cope with having this in all installations since I will end up using it at some point.

However, texlive-latex-extra recommends texlive-latex-extra-doc which adds around 250MB to my system. I'm not sure what texlive-latex-extra-doc does, but I guess it installs a bunch of help files that I don't use and I know that I can do all the things I want to do after removing it.

I know that I can install texlive-latex-extra and then remove texlive-latex-extra-doc but I would like to avoid ever installing this package (and a number of others).

Ideally I would run something like:

apt-get install texlive-latex-extra --dont-install texlive-latex-extra-doc

or perhaps

apt-get install --no-recommends texlive-latex-extra

However, I've been unable to find anything in the apt-get docs that would do this. Does anyone know of a way of doing this using apt-get or perhaps aptitude?

Thanks,
Oscar.

---

### Post by jerrrys on 2012-04-23
easy

sudo apt-get install --no-install-recommends texlive-latex-extra

[http://packages.ubuntu.com/oneiric/texlive-latex-extra](http://packages.ubuntu.com/oneiric/texlive-latex-extra)

and welcome to the forum :)

---

### Post by oscarbenjamin on 2012-05-06
Perfect.

I can see that in the man page now (I must not have been RTFMing in the wrong way somehow).

Thanks for your help.

---

