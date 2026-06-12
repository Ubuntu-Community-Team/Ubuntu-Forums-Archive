---
title: "cannot resolve"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by yazuki101 on 2008-01-29
how come when I try to do anything in recovery mode (repositories) I get this message: Cannot Resolve [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com). specifically the nvidia drivers i need to load the GUI. I am trying to load gutsy 64 bit and get a black screen when loading the normal OS from GRUB.

Specs:
-AMD x64 processor
-geforce 8600GT GPU
-gutsy gibbon 64bi alternate disk has been used

---

### Post by zvacet on 2008-01-30
Boot in recovery mode and type

```
nano /etc/apt/sources.list
```


 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com).    change to 

 [http://archive.ubuntu.com](http://archive.ubuntu.com). 

You can do this with every line in your source list.CTRL+o and Ctrl+x

---

### Post by yazuki101 on 2008-01-30
maybe a dumb question. do i edit each line and then hit crtl-o and ctrl-x, or use ctrl-o and ctrl-x

---

### Post by yazuki101 on 2008-01-30
trying to just run apt-get update, I get a whole mess of these:


Failed to fetch [http://securitty.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz](http://securitty.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz) Could not resolve 'security.ubuntu.com'

---

### Post by zvacet on 2008-01-30
> maybe a dumb question. do i edit each line and then hit crtl-o and ctrl-x

Yes,edit all lines and after that ctrl+o (overwrite=changing your source list)and ctrl+x = exit.I tryed line you post and doesn´t work for me.Or maybe you want to try this source list

> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

##Universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## Multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Backports

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Canonical Partner Repository 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

```
sudo apt-get update
```

---

### Post by dariusdwtt on 2008-04-04
I have the same problem.
I'm on a VIA/S3G and boot in text mode to get the drivers but apt gives me the same message.

Could you pleases give me any info that might help :)

Darius

---

