---
title: "How do I ad new repositories to Synaptic?"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by Pumalite on 2007-05-29
How do we renew and augment the list of repositories in 7.04?

---

### Post by taurus on 2007-05-29
You mean you want to get a new /etc/apt/sources.list?

```

deb http://archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu feisty universe
deb-src http://archive.ubuntu.com/ubuntu feisty universe

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe

deb http://archive.ubuntu.com/ubuntu feisty multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty multiverse

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu feisty-commercial main 

```

---

### Post by mythik on 2007-05-29
What about new repositories?  Does anyone know of any repositories that are not necessarily supported by Ubuntu, but contain newer version of software.

Right now I'm trying to decide whether or not I really want to put effort into gentoo/sabayon or kubuntu.  Both have their upsides, but one thing that really really bothers me is not most up to date default repositories (although I understand new stuff is what breaks systems).

---

### Post by Pumalite on 2007-05-29
> **taurus said:**
> You mean you want to get a new /etc/apt/sources.list?

```

deb http://archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu feisty universe
deb-src http://archive.ubuntu.com/ubuntu feisty universe

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe

deb http://archive.ubuntu.com/ubuntu feisty multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty multiverse

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu feisty-commercial main 

```

Thanks a lot taurus. I really appreciate the enlightenment.

---

### Post by Yoeri on 2007-05-29
Via system > administration > software sources, you have a ui to edit the sources list. You can get there via the synaptic package manager also...

---

### Post by Pumalite on 2007-05-29
> **Yoeri said:**
> Via system > administration > software sources, you have a ui to edit the sources list. You can get there via the synaptic package manager also...

Thanks a lot. That's what I really needed to know.

---

