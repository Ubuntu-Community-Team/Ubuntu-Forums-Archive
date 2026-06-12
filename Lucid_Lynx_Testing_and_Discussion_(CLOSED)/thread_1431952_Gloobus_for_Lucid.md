---
title: "Gloobus for Lucid"
date: 2010-03-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by TommyMac501 on 2010-03-17
Anyone know when Gloobus will be available for Lucid? I have tried and tried and can't get it to work.  I "know" Lucid is in Beta still, but I really think Gloobus should be integrated into it.  As far as they've taken the system, it's a shame not to have something as cool as Gloobus-preview.  I don't want to gunk up my system with KDE just to be able to have a quick glance at a proposal, invoice, letter or other file.

---

### Post by n0dix on 2010-03-17
Maybe in future releases.

---

### Post by River Jiang on 2010-03-27
Gloobus is actually working fine for me in Ludid. I simply followed the instructions on installing from source on [their website](http://gloobus.net/wiki/index.php/Install). The only thing I did differently was that I had to build and install a newer version of libspectre, from  [libspectre's project website](http://libspectre.freedesktop.org/wiki/). The libspectre-dev package that apt installs is apparently outdated.

I hope this helps.

---

### Post by shafin on 2010-03-27
I updated from intrepid with gloobus and it's been working without problems,
You can try manually downloading Karmic packages from here:
[https://launchpad.net/~gloobus-dev/+archive/gloobus-preview/+packages](https://launchpad.net/~gloobus-dev/+archive/gloobus-preview/+packages)
They work well with lucid

---

### Post by elementxyz on 2010-04-02
@River Jiang

what did you do when you came to the point where the website says:

./autogen --prefix=/usr/

mine says no file or directory. my gloobus-preview folder don't has that hidden file.

---

