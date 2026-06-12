---
title: "Missing Dependencies Prevent Install"
date: 2020-04-30
forum: Installation &amp; Upgrades
---

### Post by webmanoffesto on 2020-04-30
I've been getting frustrating dependency errors. How do I resolve these?
When I try to install the missing packages they do not install. I seem to be going in circles.

```

$ sudo apt-get -f install picard
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 fahcontrol : Depends: python-support (>= 0.90.0) but it is not installable
              Depends: python-gnome2 but it is not going to be installed
 picard : Depends: python-mutagen (>= 1.20) but it is not going to be installed
          Depends: python-libdiscid but it is not going to be installed
          Depends: libchromaprint-tools but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

$ sudo apt-get -f install python-support
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-support is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'python-support' has no installation candidate

$ sudo apt-get -f install python-gnome2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 fahcontrol : Depends: python-support (>= 0.90.0) but it is not installable
 python-gnome2 : Depends: python-gconf (= 2.28.1+dfsg-1.1) but it is not going to be installed
                 Depends: python-pyorbit (>= 2.0.1-4) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).





```

---

### Post by dino99 on 2020-04-30
which ubuntu version are you using ?  Note that python2 is on the removal road, at least for focal and up.

[https://launchpad.net/ubuntu/+source/picard](https://launchpad.net/ubuntu/+source/picard)

Be sure your sources.list match the flavour used.

---

### Post by ActionParsnip on 2020-05-01
What is the output of:

```

lsb_release -a; uname -a; apt-cache policy picard

```

Thanks

---

### Post by mc4man on 2020-05-03
picard has been python3 since after 18.04  so likely  on 18.04 or earlier,  probably  some repos disabled, check Software & Updates.

fahcontrol is also an issue, not in Ubuntu repo's , was obviously an attempted local install.

Edit: fahcontrol is python only (2.7) but again in this case likely missing Ubuntu repo's.  Seeing as though it was probably installed with dpkg you could remove it, fix repos & install . (- if on 18.04 use apt to install.

---

