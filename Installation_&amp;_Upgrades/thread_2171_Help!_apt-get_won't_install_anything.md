---
title: "Help! apt-get won't install anything"
date: 2004-10-26
forum: Installation &amp; Upgrades
---

### Post by brschmid on 2004-10-26
all i get is this error 

> Reading Package Lists... Done
Building Dependency Tree... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

it doesnt matter what i try to install, nothing works. 

help, any ideas why?

---

### Post by FLeiXiuS on 2004-10-26
Have you tried 

apt-get update
apt-get upgrade

And also make a note that it'd be a good idea to run as root.

If not that, try enabling universe for apt repo.
Edit your /etc/apt/sources.list with your favorite text editor

sudo $EDITOR /etc/apt/sources.list

Add these 2 lines to the list.
```

deb http://archive.ubuntu.com/ubuntu/ warty main restricted universe
deb-src http://archive.ubuntu.com/ubuntu/ warty main restricted universe

```

Afterwards
sudo apt-get update

---

### Post by brschmid on 2004-10-26
[QUOTE=FLeiXiuS]Have you tried 

apt-get update
apt-get upgrade

And also make a note that it'd be a good idea to run as root.

If not that, try enabling universe for apt repo.
Edit your /etc/apt/sources.list with your favorite text editor

sudo $EDITOR /etc/apt/sources.list

Add these 2 lines to the list.
```

deb http://archive.ubuntu.com/ubuntu/ warty main restricted universe
deb-src http://archive.ubuntu.com/ubuntu/ warty main restricted universe

```

Afterwards
sudo apt-get update[/QUOTE]
 i have been running them in the root terminal, is that good enough?
i will add those to lines there, i have enabled the first one in SPM.

---

### Post by Rancoras on 2004-10-26
[QUOTE=brschmid]i have been running them in the root terminal, is that good enough?[/QUOTE]

Yes, root terminal or sudo are correct.

---

### Post by jdong on 2004-10-26
Two things:

1. libdvdcss2 is **not** in ubuntu's repositories. Refer to the  official site howto's on adding the correct repository: [http://www.ubuntulinux.org/newwiki/RestrictedFormats/view](http://www.ubuntulinux.org/newwiki/RestrictedFormats/view) [see bottom about debian-marillat repository]

2. Try not to use root terminals: run as many commands with Sudo as possible. Sudo keeps a log of everything you do as root, which could greatly aid in debugging.

---

### Post by brschmid on 2004-10-26
[QUOTE=jdong]Two things:

1. libdvdcss2 is **not** in ubuntu's repositories. Refer to the  official site howto's on adding the correct repository: [http://www.ubuntulinux.org/newwiki/RestrictedFormats/view](http://www.ubuntulinux.org/newwiki/RestrictedFormats/view) [see bottom about debian-marillat repository]

2. Try not to use root terminals: run as many commands with Sudo as possible. Sudo keeps a log of everything you do as root, which could greatly aid in debugging.[/QUOTE]
 hmmm, i will try again, and report back.

---

### Post by brschmid on 2004-10-26
[QUOTE=brschmid]hmmm, i will try again, and report back.[/QUOTE]
 awesome, it works now :) thanks a lot

---

