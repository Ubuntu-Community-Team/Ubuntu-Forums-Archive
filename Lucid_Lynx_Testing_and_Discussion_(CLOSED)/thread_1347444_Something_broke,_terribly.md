---
title: "Something broke, terribly"
date: 2009-12-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by slakkie on 2009-12-06
After the KDE troubles I had, I've updated all the packages this morning and that got me into some real trouble. My machine boots, but that's about it. I cannot upgrade packages via aptitude, see below:


```

sudo aptitude update
aptitude: error while loading shared libraries: libapt-pkg-libc6.10-6.so.4.8: cannot open shared object file: No such file or directory
13:51 pts/3 127 wesleys@eniac:/home/wesleys$ sudo aptitude safe-upgrade
aptitude: error while loading shared libraries: libapt-pkg-libc6.10-6.so.4.8: cannot open shared object file: No such file or directory
13:51 pts/3 127 wesleys@eniac:/home/wesleys$ ldd $(which aptitude)
        linux-gate.so.1 =>  (0xb76e9000)
        libapt-pkg-libc6.10-6.so.4.8 => not found
        libncursesw.so.5 => /lib/libncursesw.so.5 (0xb768a000)
        libsigc-2.0.so.0 => /usr/lib/libsigc-2.0.so.0 (0xb7682000)
        libcwidget.so.3 => /usr/lib/libcwidget.so.3 (0xb75c4000)
        libept.so.0 => /usr/lib/libept.so.0 (0xb7553000)
        libxapian.so.15 => /usr/lib/libxapian.so.15 (0xb740a000)
        libz.so.1 => /lib/libz.so.1 (0xb73f5000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb73dc000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb72e8000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb72c2000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb72a4000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7160000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb715c000)
        /lib/ld-linux.so.2 (0xb76ea000)
        libapt-pkg-libc6.10-6.so.4.8 => not found
13:52 pts/3 0 wesleys@eniac:/home/wesleys$ dpkg -S libapt-pkg-libc6.10-6.so.4.8
^C
13:52 pts/3 130 wesleys@eniac:/home/wesleys$ apt-file search libapt-pkg-libc6.10-6.so.4.8
Can't load '/usr/lib/perl5/auto/AptPkg/AptPkg.so' for module AptPkg: libapt-pkg-libc6.10-6.so.4.8: cannot open shared object file: No such file or directory at /usr/lib/perl/5.10/DynaLoader.pm line 196.
 at /usr/lib/perl5/AptPkg/Config.pm line 8
Compilation failed in require at /usr/lib/perl5/AptPkg/Config.pm line 8.
BEGIN failed--compilation aborted at /usr/lib/perl5/AptPkg/Config.pm line 8.
Compilation failed in require at /usr/bin/apt-file line 28.
BEGIN failed--compilation aborted at /usr/bin/apt-file line 28.

```

Luckely dpkg still works, so I'll guess I have to install the karmic versions of apt/aptitude/dpkg..

---

### Post by Gina on 2009-12-06
There's lots of stuff being held back ATM.  They're working towards the Alpha 1 due out Thursday so it might be worth waiting until then and then reinstalling.  There will be daily builds from tomorrow (Monday) where all development is frozen except clearing bugs for the Alpha 1 ISO.  I shall probably be testing the daily builds.

---

### Post by slakkie on 2009-12-06
I'm planning on fixing this before the end of the day ;)

I got some help in #ubuntu+1, seems like there is a file missing from the apt-package. I logged a bug at lp: [https://bugs.launchpad.net/bugs/493154](https://bugs.launchpad.net/bugs/493154)

I'm now running debsums -c to check all my installed packages, it is not looking good. I didn't touch the stuff which is held back, since I do only safe-upgrades (guess not so safe after all :P).

So far debsums -c has listed over 503 missing files from packages...

---

### Post by Gina on 2009-12-06
Good luck :):)

---

### Post by slakkie on 2009-12-06
Thnx, I'll need it ;)

602 files missing from 224 packages.

---

### Post by xebian on 2009-12-06
Looks like kde 4.4 B1 is currently being uploaded.  I tried the kubuntu-ppa/staging and it's un-useable.

If you want to see how 4.4B1 is, there is a pretty good live-cd here

[http://kde4.livecd.pld-linux.org/](http://kde4.livecd.pld-linux.org/)

---

### Post by slakkie on 2009-12-06
I managed to fix apt, and then I could go about reinstalling 224 packages.
I haven't booted yet, but I suspect better results :)

---

### Post by juanJosepablos on 2009-12-06
well, I  download the daily live and a couple of days, I was able to install with not problems at all, yesterday version is not even able to get an ip using dhclient. I am getting a libc.so.6 not found error.

---

### Post by slakkie on 2009-12-06
OK, I can do more now, but my KDE problems remain. I've tried installing the debugging packages, but I've allocated too little space..

---

