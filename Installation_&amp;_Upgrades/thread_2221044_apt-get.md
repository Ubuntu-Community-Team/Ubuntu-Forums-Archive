---
title: "apt-get"
date: 2014-04-30
forum: Installation &amp; Upgrades
---

### Post by mayagrafix on 2014-04-30
when I run apt-get install I get the following message:
> 
The following packages were automatically installed and are no longer required:
  blt cgroup-lite comerr-dev indicator-sync libamd2.2.0 libboost-date-time1.53.0 libboost-filesystem1.53.0
  libboost-iostreams1.53.0 libboost-regex1.53.0 libboost-signals1.53.0 libboost-system1.53.0 libboost-thread1.53.0
  libcmis-0.3-3 libcolamd2.7.1 libdb5.1:i386 libdee-qt5-3 libdns99 libebackend-1.2-6 libebml3 libedata-book-1.2-17
  libedata-cal-1.2-20 libfftw3-3 libfftw3-long3 libgcrypt11-dev libgnutls-dev libgnutlsxx27 libgpg-error-dev
  libgweather-3-3 libhud-client2 libidn11-dev libkadm5clnt-mit8 libkadm5clnt-mit9 libkadm5srv-mit8 libkdb5-6
  liblcms1:i386 libldap2-dev libllvm3.3 libllvm3.3:i386 libmatroska5 libmjpegutils-2.0-0 libmng1:i386
  libmpeg2encpp-2.0-0 libmplex2-2.0-0 libp11-kit-dev libpoppler43 libppl12 libpthread-stubs0 libpython3.3
  libpython3.3-minimal libpython3.3-stdlib libqpdf10 libqt4-dbus:i386 libqt53d5 libqt5location5 libqt5v8-5
  librhythmbox-core7 librtmp-dev libseccomp1 libtasn1-3:i386 libtasn1-3-dev libtasn1-6-dev libtcl8.5 libtk8.5
  libumfpack5.4.0 libwebp4 libxcb-sync0 linux-image-3.11.0-12-generic linux-image-3.13.0-20-generic
  linux-image-extra-3.11.0-12-generic linux-image-extra-3.13.0-20-generic openbox-themes python-central
  python-imaging-compat python-m2crypto python3.3 python3.3-minimal tcl8.5 tclx8.4 tk8.5 wine-gecko1.4
  wine-gecko1.4:i386 wine1.4 wine1.4-amd64 wine1.4-i386:i386

**Use 'apt-get autoremove' to remove them.**
The last time I ran apt-get autoremove it broke my system and had to re-install Ubuntu from CD. But that was a long time ago and probably my fault. Should I run apt-get autoremove again?

---

### Post by ian-weisser on 2014-04-30
Since we don't know anything about your system, nor what you want to keep, I think you are asking us to be a bit psychic.

Do you use Python 3.3, or has your system upgraded to 3.4?
Do you use Wine?
Is your running kernel later than 3.13.0-20?
Have you looked at the list to see what you recognize?

---

### Post by sudodus on 2014-04-30
I would say that if you have run
```

sudo apt-get update
sudo apt-get dist-upgrade

```
and everything looks good, you can use autoremove.

See ```
man apt-get
```

```
       clean
           clean clears out the local repository of retrieved package files. It removes everything but
           the lock file from /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When APT
           is used as a dselect(1) method, clean is run automatically. Those who do not use dselect
           will likely want to run apt-get clean from time to time to free up disk space.

       autoclean
           Like clean, autoclean clears out the local repository of retrieved package files. The
           difference is that it only removes package files that can no longer be downloaded, and are
           largely useless. This allows a cache to be maintained over a long period without it growing
           out of control. The configuration option APT::Clean-Installed will prevent installed
           packages from being erased if it is set to off.

       autoremove
           autoremove is used to remove packages that were automatically installed to satisfy
           dependencies for other packages and are now no longer needed.

```

The manual explains what apt-get autoremove is doing. I often run

```

sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean

```
to get more free space in the root partition. I have never had any problems with any of the commands.

---

### Post by bapoumba on 2014-04-30
This means that the packages were automatically installed as dependencies of (an)other package(s). If you removed this or these other package(s), they can be also removed (automatically, all of them at once) because the package(s) needing them is not longer on your system.

Now if you removed a metapackage (some are used to ease linking parts of the distribution such as core apps or desktop apps) you may end up removing stuff you need.
What I can tell you is that python-minimal and libpython3.4-minimal are installed on my system (you must be on saucy as you have the 3.3 libs), and these are maintained by core developers.

---

