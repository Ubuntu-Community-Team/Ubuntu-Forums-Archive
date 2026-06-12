---
title: "Installing vlc from .deb files"
date: 2006-09-13
forum: Installation &amp; Upgrades
---

### Post by czk101 on 2006-09-13
I'm new to linux, but have set up a linux server and want to install vlc on it I want to install an old version (0.7.2) as i want to be able to broadcast to my dbox2 (which wont work with 0.8.x versions)

I've got all the .deb files from here [http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/](http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/)
and then spent ages sorting dependencies (nightmare!)

I used dpkg -i package.deb to install everything, which it did without errors, but now if i try and run vlc from the command line using vlc i get the error message

-bash: /usr/local/bin/vlc: no such file or directory

Any ideas on how to correct this?

Thanks

---

### Post by whizbaby on 2006-09-13
You would have to find it (first look if it's not in */usr/bin*):
[B]sudo updatedb
locate vlc|grep bin[/B]

Let's say it's in /usr/bin (if not replace with what you found). Do
**ln -s */usr/bin/vlc /usr/local/bin/vlc***
to create a link.
(besides you can install older versions with apt-get simply by giving the whole package name (including version, without *.deb*))

---

### Post by czk101 on 2006-09-13
Thank you, that has sorted my problem.

Tried apt-get with full name, but didnt seem to work

---

### Post by whizbaby on 2006-09-13
It is because I was unprecise (here out of *man apt-get*):
```

A specific version of a package can be selected for installation
              by  following the package name with an equals and the version of
              the package to select. This will cause that version to be locat&#8208;
              ed  and selected for install. Alternatively a specific distribu&#8208;
              tion can be selected by following the package name with a  slash
              and the version of the distribution or the Archive name (stable,
              testing, unstable).
```

That means if you want to get version *1:2.5-0ubuntu10* of the package *barefoo* (doesn't exist) you'll have to type

**sudo apt-get install *barefoo=1:2.5-0ubuntu10***

---

