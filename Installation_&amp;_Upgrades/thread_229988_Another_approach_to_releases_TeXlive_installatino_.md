---
title: "Another approach to releases? TeXlive installatino painful"
date: 2006-08-05
forum: Installation &amp; Upgrades
---

### Post by DeHa on 2006-08-05
Hello!

I'm a beginning TeX user and at home I used to have Debian unstable with texlive-full package. Currently I'm at my girlfriend's who uses Ubuntu Dapper Drake.

I wanted to compile some document, which needed a LaTeX package. This package was not found in the dapper repository and I have no idea what's the proper way to install TeX/LaTeX packages on Ubuntu (are there to be debianised somehow or installed under $HOME or /usr/local or whatev).

Therefore I decided to backport texlive packages myself. After pulling source of all texlive packages and building it, then packages like tex-common, lmodern, then xfonts-base, defoma, debhelper, dpkg-dev, libdelinux... I said 'no' and didn't wanted to go further.

I found the only way to use this one lonely package is to upgrade to edgy eft (which is unstable and I would rather her having a stable distro).

So here are my propositions:
1. Found a better approach to releases. Eg. if one package (texlive for example) works for unstable then push it into backports. Then if it works tehre too push it further to stable. This way we don't have to wait half a year till the next release to get a new package or more recent version of one used

2. Write a HOWTO about installing custom TeX/LaTeX packages.

3. Create a debianiser for said. (Then one could just dpkg -i tex-package.deb)

4. Create a nice and smart GUI for installing above said. If only a 2. point is achieved I could write some GUI for it, but since I have no idea how to install these packages I'd rather stick to repository.

Another thing is that some TeX packages in this texlive-* packages are extremely old (yes, about a year is a looooong time here, in software). But that's probably for another post.

---

### Post by jordilin on 2006-08-05
take a look here:
[http://www.ubuntuforums.org/showthread.php?t=226332](http://www.ubuntuforums.org/showthread.php?t=226332)
it explains how to install the latest in latex.

---

