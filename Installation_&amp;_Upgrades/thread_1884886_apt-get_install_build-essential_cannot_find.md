---
title: "apt-get install build-essential cannot find"
date: 2011-11-22
forum: Installation &amp; Upgrades
---

### Post by Hanfraucher on 2011-11-22
Hi Folks
 
I'm in process of installing ubuntu. Since I wanna learn a bit more about linux I do it the manual way. I got stuck and would appreciate some help.
 
What I did:
 
From Petitboot I made 2 partitions, mounted it and bootstraped ubuntu:
 
debootstrap --arch powerpc lucid /mnt/ubuntu [http://ports.ubuntu.com](http://ports.ubuntu.com)
 
then I switched over, set fstab, network and language settings.
 
in /etc/apt/sources.list I set the following:
 
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid-updates main restricted
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid-updates restricted
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid universe
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid-updates universe
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid multiverse
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid-updates multiverse
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid-security main restricted
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid-security main restricted
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid-security universe
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid-security universe
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid-security multiverse
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid-security multiverse
 
apt-get update runs fine without errors
 
I can get packages like nano, locales, console-data fine without a hitch
 
But when I want to compile a kernel, I get errors that the packages could not be found (diffrent from false spelled name)
 
command I use:
 
apt-get install build-essential ncurses-dev git-core gitosis
 
 
and since git does not install on the follow up command:
 
git clone --depth=1 git://git.gitbrew.org/ps3/ps3linux/linux-2.6.git
 
i get error: git unknown command
 
 
 
 
 
Are there additional /etc/apt/sources.list sources? I couldnt find more and the documentation I use ([http://wiki.gitbrew.org/wikibrew/PS3:Linux#Ubuntu](http://wiki.gitbrew.org/wikibrew/PS3:Linux#Ubuntu)) just listed those. I done the whole process now twice with same result.
 
 
thanks in advance

---

### Post by gordintoronto on 2011-11-22
I think you missed lucid main and restricted.

---

### Post by Hanfraucher on 2011-11-23
Ok thanks. Tried it and worked.

---

