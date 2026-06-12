---
title: "Installing *just* ubuntu-minimal?"
date: 2006-09-13
forum: Installation &amp; Upgrades
---

### Post by rdr on 2006-09-13
Hi,

I want a very *basic* base system and want to install just ubuntu-minimal. How do I go about doing this? I tried with the following preseed and the dapper server CD, but it doesn't seem to work.

Help!!

[SIZE="1"]# Always install the server kernel.
d-i     base-installer/kernel/override-image    string linux-server
# Don't install usplash.
d-i     base-installer/kernel/linux/extra-packages-2.6  string
# Desktop system not installed; don't waste time and disk space copying it.
d-i     archive-copier/desktop-task     string ubuntu-minimal
d-i     archive-copier/ship-task        string
# Only install the standard system and language packs.
d-i     pkgsel/install-pattern  string ~t^ubuntu-minimal$
d-i     pkgsel/language-pack-patterns   string
# No language support packages.
d-i     pkgsel/install-language-support boolean false
[/SIZE]

---

### Post by lambot on 2006-09-13
You can try ubuntu-alternate cd with it's *server installation* - there are no reall server appz there, just base packs

---

### Post by rdr on 2006-09-13
> **lambot said:**
> You can try ubuntu-alternate cd with it's *server installation* - there are no reall server appz there, just base packs

But that still goes to over 220MB. Is that the smallest Ubuntu Dapper install possible without any manual intervention?

---

### Post by orb9220 on 2006-09-13
That's all for HD space?

---

### Post by rdr on 2006-09-13
> **orb9220 said:**
> That's all for HD space?

Yes.. 220MB is occupied in the partition.

I want to trim things down to less than 50MB and still have apt/dpkg working. 

A huge part of this was the kernel+modules. I've now got a module-less kernel compiled with the required drivers and cut nearly 60MB out of it. 

But it is still too big. 

ubuntu-minimal package description states that it is the minimum required to boot and connect to a network.. and it is supposed to be only 40MB.. so, was wondering if that would work. :)

---

### Post by Zed on 2006-09-22
You can install just ubuntu-minimal With tons of manual intervention using [debootstrap](http://www.linux.com/article.pl?sid=06/08/17/1947210).

```

debootstrap --arch i386 dapper /mnt/whatever http://archive.ubuntu.com/ubuntu

```

I've done this. ubuntu-minimal is really minimal. When I realized I didn't even have man pages, I quickly installed [ubuntu-standard.](http://packages.ubuntu.com/dapper/base/ubuntu-standard)

---

