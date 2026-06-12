---
title: "a list of alternate repositories"
date: 2018-07-13
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2018-07-13
does anyone know of a list of alternate repositories that offer alternate packages or package versions for older Ubuntu (still in support), such as 16.04 LTS, that the official repositories do not have?  for example i was looking for one that had a more recent version of Python (such as 3.7.0).

---

### Post by oldos2er on 2018-07-14
[https://launchpad.net/~deadsnakes/+archive/ubuntu/ppa/+packages](https://launchpad.net/~deadsnakes/+archive/ubuntu/ppa/+packages)

Personally I'd be concerned installing a later python version would mess something up.

---

### Post by TheFu on 2018-07-14
> **Skaperen said:**
> does anyone know of a list of alternate repositories that offer alternate packages or package versions for older Ubuntu (still in support), such as 16.04 LTS, that the official repositories do not have?  for example i was looking for one that had a more recent version of Python (such as 3.7.0).

Anyone can make a PPA. You can make one, if you like.   That makes having a complete list of repos effectively impossible.  The best way to find them that I know is google.   But only PPAs from trusted people/groups should be used. Avoid random PPAs.  Reputation is really the only way I know to determine if someone is worthy of trust. If you wouldn't give the PPA owner root on your Linux machine, then you shouldn't use the PPA.  Using a PPA is effectively providing the packaging people with local root.

As  oldos2er says, if you want a different version of any scripting language, then you should NOT replace it at the OS level, but make a separate are just for that version. Most scripting languages have a way to install 2,5,20 versions of their software so custom development is separate from the OS.  This is a best practice.

I don't use python, but Ruby has rbenv and rvm.  Perl has Perlbrew. I'm positive that python has something similar, pyenv. [https://github.com/pyenv/pyenv](https://github.com/pyenv/pyenv) seems to be it. There might be other alternatives too.

---

