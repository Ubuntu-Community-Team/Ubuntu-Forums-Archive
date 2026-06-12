---
title: "Doubts on repositories"
date: 2004-10-15
forum: Installation &amp; Upgrades
---

### Post by slamdunk on 2004-10-15
Hi,

I have installed ubuntu, and I use normally synaptic to install packages on my system.
I have doubts on repositories list.
What is exactly the difference for warty, warty-security and warty-updates???

I'm interested to have a system updated to last packages. In Mandrake or Fedora I can install last package (for example gaim 1.0.1 or others) but with ubuntu packages is not possibile for me. What's exact repositories to do it?

Exists an extra-repository with no-free packages (example: mplayer-plugins, mplayer codecs, flash plugin, etc)??

Thank you very much
Giulio

---

### Post by oddabe19 on 2004-10-15
edit your /etc/apt/sources.list and uncomment the two universe options.

Then do an ```
sudo apt-get update &amp;&amp; sudo apt-get upgrade
``` and you'll be up to the latest, and you'll have a bunch of packages available that aren't available in the other servers

---

### Post by slamdunk on 2004-10-15
It's not work. This is my source.list:

deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Unofficial i386 Binary-1 (20040915)]/ unstable main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe

## Uncomment the following two lines to fetch updated software from the network
## and be able to use more than 12000 unsupported packages from the universe archive.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted universe

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty-updates main restricted universe




deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty-updates main restricted universe

Thanks
Giulio

---

### Post by HungSquirrel on 2004-10-15
You've got two copies of the same repository.  Apt doesn't like that.  Comment out or remove the top copies, save, then *apt-get update*.

---

### Post by slamdunk on 2004-10-16
yes thanks:)
however my packages are old again:(
Maybe ubuntu is not fast-updated like mandrake fedora gentoo etc?

Thanks
Giulio

---

### Post by Damon on 2004-10-16
[quote=slamdunk]yes thanks:)
however my packages are old again:(
Maybe ubuntu is not fast-updated like mandrake fedora gentoo etc?

Thanks
Giulio[/quote]
I wouldn't go that far. The software packages are just managed differently. Ubuntu is a debian based distrobution. Check out [http://www.debian.org/doc/manuals/debian-tutorial/ch-dpkg.html](http://www.debian.org/doc/manuals/debian-tutorial/ch-dpkg.html) for a little reading.

(I'm a debian newb, too...)

---

