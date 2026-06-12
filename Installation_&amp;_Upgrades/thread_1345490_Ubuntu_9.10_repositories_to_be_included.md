---
title: "Ubuntu 9.10 repositories to be included"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by ddas4 on 2009-12-04
Hello,
 
I am new to Ubuntu world but not to the linux universe. I have been using OpenSuse. I am planning to move over to Ubuntu in place of OpenSuse. There were standard tips floating on OpenSuse forums about which repos to include on top of your standard repos. Like : add packman repo to get all your multimedia needs and pull all your media packages from there ; include only updates, OSS, Non-OSS from standard repo ; get libdvdcss 'only' from VLC repo and then disable it ; etc.
 
Wanted to know if something like this existed at a single location , with crisp instructions on how to handle the repos. So to be exact; which repositories should i include (if at all) for my:
1. multimedia needs: gstreamers good,bad,ugly, w32codecs, other restricted formats, xine, mplayer, songbird, Banshee, VLC-music players UI & plugins, etc.
2. acroread, hplip, metamorphose2, aMSN, skype, ddclient, empathy-sametime, java & its plugins, Microsoft ttf, avidemux
 
One of my Fedora installations had got messed up from point of view of multimedia just because the repos were not selected properly.
 
Need to be very sure of this before i switch over. Appreciate your help !

---

### Post by hal10000 on 2009-12-04
Try the [ubuntu sources listgenerator]("http://repogen.simplylinux.ch/")

[This]("https://help.ubuntu.com/9.10/add-applications/C/adding-repos.html") may also be useful for you.

---

### Post by slakkie on 2009-12-04
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

You might want to have a look that page.  These are my default repo's. Replace lucid with karmic if you are installing 9.10

```

## Keepers
deb http://archive.ubuntu.com/ubuntu/ lucid main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ lucid main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu lucid-security main restricted universe multiverse
# deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted universe multiverse

## Optional, but recommended
deb http://archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe multiverse

## Optional, remove if you don't like them
deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://archive.ubuntu.com/ubuntu/ lucid-proposed main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ lucid-proposed main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Medibuntu repositories, check http://www.medibuntu.org/ for more details
deb http://packages.medibuntu.org/ lucid free non-free
#deb-src http://packages.medibuntu.org/ lucid free non-free
deb http://packages.medibuntu.org/ karmic free non-free
#deb-src http://packages.medibuntu.org/ karmic free non-free
#deb http://packages.medibuntu.org/ jaunty free non-free
#deb-src http://packages.medibuntu.org/ jaunty free non-free

```

---

### Post by ddas4 on 2009-12-04
Thanks for your responses. Gives good directions to start with !

---

### Post by ddas4 on 2009-12-07
I did install Ubuntu 9.10 over the weekend and it was a smooth ride with the repos. Thanks for all your tips.

---

