---
title: "Where are packages in Edgy?"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by roncrump on 2006-11-05
hi,

I've just done a completely clean install of Ubuntu 6.10.

Then I changed my /etc/apt/sources.list file as per instructions on customising for Australia:

```
## All officially supported packages, including security- and other updates
deb http://ftp.iinet.net.au/pub/ubuntu/ edgy main restricted
deb http://ftp.iinet.net.au/pub/ubuntu/ edgy-security main restricted
deb http://ftp.iinet.net.au/pub/ubuntu/ edgy-updates main restricted

## The source packages (only needed to recompile existing packages)
#deb-src http://ftp.iinet.net.au/pub/ubuntu/ edgy main restricted
#deb-src http://ftp.iinet.net.au/pub/ubuntu/ edgy-security main restricted
#deb-src http://ftp.iinet.net.au/pub/ubuntu/ edgy-updates main restricted

## All community supported packages, including security- and other updates
deb http://ftp.iinet.net.au/pub/ubuntu/ edgy universe multiverse
deb http://ftp.iinet.net.au/pub/ubuntu/ edgy-security universe multiverse
deb http://ftp.iinet.net.au/pub/ubuntu/ edgy-updates universe multiverse

## The source packages (only needed to recompile existing packages)
#deb-src http://ftp.iinet.net.au/pub/ubuntu/ edgy universe multiverse
#deb-src http://ftp.iinet.net.au/pub/ubuntu/ edgy-security universe multiverse
#deb-src http://ftp.iinet.net.au/pub/ubuntu/ edgy-updates universe multiverse
```

Now I do not seem to be able to find a number of packages that I need to install, sudo apt-get install <package> reports the package isn't found.

Packages in question include gfortran, scilab, r-base (and other R related) and latex distributions (tetex or texlive). At least gfortran and r-base are listed on packages.ubuntu.com as being in universe, which looks to me to be active, so where are they? What have I messed up?

Thanks,
Ron.

---

### Post by MWAAAHAAA on 2006-11-05
Did you by any chance forget to run 'apt-get update'?

---

### Post by roncrump on 2006-11-05
> **MWAAAHAAA said:**
> Did you by any chance forget to run 'apt-get update'?

:oops: You're quite right, of course.
All good now. Thanks.

---

