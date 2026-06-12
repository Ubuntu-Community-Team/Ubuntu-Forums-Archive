---
title: "Need help with vrml viewer program"
date: 2006-12-22
forum: Installation &amp; Upgrades
---

### Post by liveder on 2006-12-22
Hi all,


I've tried to run a vrml viewer program (vrmlview) but it seems that I'm missing libstdc++-libc6.1-1.so.2

```

me@my_computer ~ # vrmlview
vrmlview: error while loading shared libraries: libstdc++-libc6.1-1.so.2 cannot open shared object file: No such file or directory

```


I have libstdc++ installed
```

me@my_computer ~ # locate libstdc++ | grep -v src
/var/lib/dpkg/info/libstdc++5.list
/var/lib/dpkg/info/libstdc++6.list
/var/lib/dpkg/info/libstdc++6.md5sums
/var/lib/dpkg/info/libstdc++6-4.1-dev.md5sums
/var/lib/dpkg/info/libstdc++6.postrm
/var/lib/dpkg/info/libstdc++6.shlibs
/var/lib/dpkg/info/libstdc++5.postinst
/var/lib/dpkg/info/libstdc++5.md5sums
/var/lib/dpkg/info/libstdc++6.postinst
/var/lib/dpkg/info/libstdc++6-4.1-dev.list
/var/lib/dpkg/info/libstdc++5.postrm
/var/lib/dpkg/info/libstdc++5.shlibs
/var/cache/apt/archives/libstdc++6-4.1-dev_4.1.1-13ubuntu5_i386.deb
/usr/lib/gcc/i486-linux-gnu/4.1.2/64/libstdc++.so
/usr/lib/gcc/i486-linux-gnu/4.1.2/64/libstdc++.a
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.a
/usr/lib/libstdc++.so.5
/usr/lib/libstdc++.so.6
/usr/lib/libstdc++.so.5.0.7
/usr/lib/libstdc++.so.6.0.8
/usr/share/doc/libstdc++5
/usr/share/doc/libstdc++5/README.Debian
/usr/share/doc/libstdc++5/copyright
/usr/share/doc/libstdc++5/changelog.Debian.gz
/usr/share/doc/libstdc++6
/usr/share/doc/gcc-4.1-base/C++/changelog.libstdc++.gz
/usr/share/doc/gcc-4.1-base/C++/README.libstdc++-baseline
/usr/share/doc/gcc-4.1-base/C++/libstdc++_symbols.txt
/usr/share/doc/libstdc++6-4.1-dev

```


I've tried to do a libstdc++-libc6.1-1.so.2 symlink to both versions of libstdc++, but now I get

```

me@my_computer lib > vrmlview
vrmlview: symbol lookup error: vrmlview: undefined symbol: __builtin_new

```


Does someone knows how to solve this?

---

### Post by jsym on 2008-03-03
I know you posted this a long time ago, but I had a very similar problem.  On the off chance that you never fixed this, you might find looking at [[COLOR="Blue"]_this post_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=425279") helpful.

---

### Post by jsym on 2008-03-04
Ignore the previous post, it won't help as I discovered when I tried to install the same software on my own machine.

I found another post that was much more helpful [[COLOR="Blue"]_HERE_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=237829").

The symlink won't work because the things that [[COLOR="Blue"]_vrmlview_[/COLOR]]("http://www.km.kongsberg.com/ks/web/nokbg0237.nsf/AllWeb/E1DB099B3F91AC26C12572DB004D4EE1?OpenDocument") wants to be in the library and the things actually in the library that might be linked to are not the same.

Here is what I ended up doing:
```
$ mkdir temp
$ cd temp
$ wget ftp://rpmfind.net/linux/PLD/dists/ra/PLD/i686/PLD/RPMS/libstdc++-compat-1.0-6.i686.rpm
$ sudo alien --to-tgz libstdc++-compat-1.0-6.i686.rpm
$ tar zxf libstdc++-compat-1.0.tgz
$ cd usr/lib
$ sudo cp libstdc++-2-libc6.1-1-2.9.0.so /usr/lib32/libstdc++-libc6.1-1.so.2

```
Of course, you will need alien to make this work.  It is readily available from Synaptic.

---

