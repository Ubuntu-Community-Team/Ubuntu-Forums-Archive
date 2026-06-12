---
title: "using Debian repositories?"
date: 2006-12-02
forum: Installation &amp; Upgrades
---

### Post by guano on 2006-12-02
Hello there. I am trying to install GRASS-GIS 6.2 (grass.itc.it) from debian.gfoss.it, since the version in Ubuntu is too old (6.0.2), but I have some dependencies problem, which can be solved if I use the official Debian repository, but I don't know how. I tried to include packages.debian.org in my sources.list, but I have a problem with the pgp key.
Where can I get the pgp key for debian?
what is the right repo I should include in my sources.list?

thanks

---

### Post by bapoumba on 2006-12-02
Hello,
first, I do not know anything about grass-gis ;)
You have a tar.gz [here]("http://linux.softpedia.com/get/Science-and-Engineering/Geographical/GRASS-GIS-2385.shtml"). 
I have not downloaded the file, but there should be a readme file coming along with instructions.

It is not recommended to mix up repositories from different distributions, unless you exactly know what you are doing and you know how to get yourself out of broken dependencies.

---

### Post by Rui Pais on 2006-12-02
hi,
a lot of people arount want grass these days :lol:

[This is not about grass-gis but grass alone]("http://ubuntuforums.org/showthread.php?p=1827301#post1809929"). Haven't the faintest idea whats the difference (all grass for me...) but the principle should be the same.

Maybe it helps solving the dependency problems.

---

### Post by az on 2006-12-02
> **guano said:**
> Hello there. I am trying to install GRASS-GIS 6.2 (grass.itc.it) from debian.gfoss.it, since the version in Ubuntu is too old (6.0.2), but I have some dependencies problem, which can be solved if I use the official Debian repository, but I don't know how. I tried to include packages.debian.org in my sources.list, but I have a problem with the pgp key.
Where can I get the pgp key for debian?
what is the right repo I should include in my sources.list?

thanks
Compile it from source if you want it - the debian and ubuntu repos are not binary-compatible.

Add the deb-src line for debian and 
sudo apt-get build-dep (package)

apt-get -b source (package)

---

### Post by guano on 2006-12-02
Well, bapoumba says that doesn't knows anything about GRASS, but I know. I've been using this excelent GIS software for a few years now. 

So the point is:

I CAN compile it. I've been doing this for about four years. The fact is that right know I am kinda lazy so I don't want top compile it. Pure and Simple.

All I want is to install it via apt.

The problem is that using gfoss.debian.it, I get a dependency error (with GDAL), and if I could use de main Debian repos, this dependency error would be solved, but I don't have the key fingerprint for the Debian repos. Got it?

That's my problem. It's not about install GRASS from dource or from apt, is about how to get the bloody fingerprint for Debian main site!

Carlos

---

### Post by az on 2006-12-02
> **guano said:**
> 
The problem is that using gfoss.debian.it, I get a dependency error (with GDAL), and if I could use de main Debian repos, this dependency error would be solved, but I don't have the key fingerprint for the Debian repos. Got it?

You don't want to get any binary packages from debian repos.  Got it?

---

### Post by guano on 2006-12-02
> **azz said:**
> You don't want to get any binary packages from debian repos.  Got it?

No. I do want to use binaries from Debian repo. The thing is that I need the key fingerprint to acces the Debian repos. that's what I don't have.

---

