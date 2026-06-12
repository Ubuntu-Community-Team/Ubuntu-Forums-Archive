---
title: "No package 'gtk+-2.0' found error message"
date: 2006-11-22
forum: Installation &amp; Upgrades
---

### Post by timcredible on 2006-11-22
While trying to compile xmpcr2 (an XM radio PCR application), I get the above error message.  I searched around, installed build-essentials via synaptic, but still get the error.  I also had to install automake and autoconf and g++ to get this far.  I'm using ubuntu 6.10.  I have the xmpcr2 app running on a different machine with pclos, so I know the app will run.  If anyone knows what package I'm missing, I'd appreciate it.  Thanks.

---

### Post by taurus on 2006-11-22
First, it's build-essential (without the _s_ at the end).
Second, exactly what's the error message when you try to build it?

---

### Post by timcredible on 2006-11-22
Here's a copy-paste:

checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 >= 2.0.0) were not met:

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by taurus on 2006-11-22
Use synaptic and search for gtk+-dev package...

---

### Post by timcredible on 2006-11-22
not finding that.  could it be called something else?  Thanks.

i can't believe i forgot to mention this - i actually installed linuxmint 2.0 on this one (I've been working with ubuntu 6.10 on a couple other PCs, but this one has linuxmint 2.0 on it).  does this make a difference with default repos - is that why i'm not finding the package?

---

### Post by taurus on 2006-11-22
If you think it's the repos, then let's have a look at them then!

```
cat /etc/apt/sources.list
```

---

### Post by timcredible on 2006-11-22
```

deb http://us.archive.ubuntu.com/ubuntu/ edgy main universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```

---

### Post by taurus on 2006-11-22
I would include all the universe and multiverse repos as well...

```

deb http://us.archive.ubuntu.com/ubuntu/ edgy main universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main  restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```
Then,

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by timcredible on 2006-11-22
that didn't work either.  i got lazy and ended up just copying the executable from the machine that had it working to the ubuntu machine, and it's working ok.  Thanks for the help though, I've just started working with ubunutu (been using plcos for the last year, mepis before that, fedora, redhat, slackware before that, dating back to 94), and hopefully I'll get up to speed quickly.

---

