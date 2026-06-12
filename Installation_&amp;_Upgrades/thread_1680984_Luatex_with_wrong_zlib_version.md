---
title: "Luatex with wrong zlib version"
date: 2011-02-03
forum: Installation &amp; Upgrades
---

### Post by x5x_tim on 2011-02-03
I'm trying to install latex. (I'm using the packages tex-common, tex-base and tex-bin)
However, installation fails.
When I dug up the error log, I found out that the error was in this command (and others like it):
```
$luatex -ini   -jobname=luatex -progname=luatex luatex.ini

PANIC: unprotected error in call to Lua API (zlib library version does not match - header: 1.2.3.3, library: 1.2.5)
```

What should I do?
I already tried downgrading my zlib but that didn't work.
Should I remove zlib and try to install 1.2.3.3 or is there a way to remove the check from luatex?

Any help would be greatly appreciated - I have a few papers to turn in ;)

---

### Post by ptn107 on 2011-02-03
Are you running Ubuntu 10.04.1?  Depending on what Ubuntu you have installed your zlib1g version would be as such:

Ubuntu 8.04.4 (hardy)   - 1.2.3.3.dfsg-7ubuntu1
Ubuntu 9.10 (karmic)    - 1.2.3.3.dfsg-13ubuntu3
Ubuntu 10.04.1 (lucid)  - 1.2.3.3.dfsg-15ubuntu1
Ubuntu 10.10 (maverick) - 1.2.3.4.dfsg-3ubuntu1

Seems you have the latest release installed from the website[1].  You should go back to the version supplied by hardy, karmic, or lucid.

[1] [http://www.zlib.net/](http://www.zlib.net/)

---

### Post by x5x_tim on 2011-02-03
I just apt-get removed 'zlib-bin'.
When I try to remove zlib1g, I get a huge list of packages that I don't really wanna remove.
How do I install zlib-bin-1.2.3.3?

---

### Post by x5x_tim on 2011-02-03
Oh, by the way, I am using 10.04.1 LTS

---

### Post by x5x_tim on 2011-02-04
bump

---

### Post by x5x_tim on 2012-01-21
I just gave it another try. I replaced my zlib with the PPA here [[https://launchpad.net/ubuntu/+source/zlib]](https://launchpad.net/ubuntu/+source/zlib]) and texlive installed successfully.

---

### Post by bernpuc on 2013-01-23
I am having the same issue and have the expected zlib libraries installed:
ii  zlib1g                               1:1.2.3.3.dfsg-15ubuntu1                        compression library - runtime
ii  zlib1g-dev                           1:1.2.3.3.dfsg-15ubuntu1                        compression library - development

Not sure how to solve this since there doesn't seem to be any problems with the installed versions - the system is updated to latest version of all packages for 10.04.4 LTS.

---

