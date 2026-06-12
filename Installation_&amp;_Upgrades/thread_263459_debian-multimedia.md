---
title: "debian-multimedia"
date: 2006-09-23
forum: Installation &amp; Upgrades
---

### Post by rikhard.fsoss on 2006-09-23
hi all,

I'm using automatix, but it seems that [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) has more updated packages that the source.list of automatix, example: dvdrip 0.52.5 with automatix.

and with [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) i got:

Version: 1:0.98.1-0.1
Priority: optional
Section: graphics
Maintainer: Christian Marillat <marillat@debian.org>

but i can't install the later one, it conflicts.

so how can i use Christian Marillat <marillat@debian.org> packages in kubuntu?

thanks in advance.

Rikhard.fsoss:confused:

---

### Post by tseliot on 2006-09-23
> **rikhard.fsoss said:**
> hi all,

I'm using automatix, but it seems that [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) has more updated packages that the source.list of automatix, example: dvdrip 0.52.5 with automatix.

and with [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) i got:

Version: 1:0.98.1-0.1
Priority: optional
Section: graphics
Maintainer: Christian Marillat <marillat@debian.org>

but i can't install the later one, it conflicts.

so how can i use Christian Marillat <marillat@debian.org> packages in kubuntu?

thanks in advance.

Rikhard.fsoss:confused:

You might want to recompile it.

**[COLOR="Red"]NOTE: TRY THIS AT YOUR RISK[/COLOR]**

Remove that repo from your sources.list and add the following:
```
deb-src http://www.debian-multimedia.org sid main
```

Then type:
```
sudo apt-get update
```

Install everything you need to compile it:
```
sudo apt-get build-dep dvdrip
```

Then make a new directory and build the package there:
```
mkdir dvdrip
```
```
cd dvdrip
```
```
sudo apt-get source -b dvdrip
```

If it goes well, you can then type:
```
sudo dpkg -i *.deb
```

---

### Post by rikhard.fsoss on 2006-09-23
thanks for the answer.

but do i have to compile every thing that i want from debian-multimedia, like transcode etc?

why can't i simply #aptitude install package?

can you please explain?

thanks

---

### Post by rikhard.fsoss on 2006-09-23
it compiled ok but can't install.

this package libgtk-pixbuf-perl should be libgdk-pixbuf-perl instead.

it seems yhat there is a bug in the package name....:-(

---

### Post by tseliot on 2006-09-24
> **rikhard.fsoss said:**
> it compiled ok but can't install.

this package libgtk-pixbuf-perl should be libgdk-pixbuf-perl instead.

it seems yhat there is a bug in the package name....:-(

It's a dependency problem. You should give in since the repository is for Debian.

---

### Post by rikhard.fsoss on 2006-09-24
it seems so.... :-( thanks

---

