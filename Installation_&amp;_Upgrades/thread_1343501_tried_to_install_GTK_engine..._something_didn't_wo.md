---
title: "tried to install GTK engine... something didn't work"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by clockworktri on 2009-12-01
I tried to install aurora 1.5 engine and went through "./configure --prefix=/usr --enable-animation" and "make" fine, but when i entered "make install",  the terminal said this:

make[1]: Entering directory `/home/renee/GTK stuff/ENGINES/56438-aurora-1.5.1/aurora-1.5'
make[1]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/gtk-2.0/2.10.0/engines" || /bin/mkdir -p "/usr/lib/gtk-2.0/2.10.0/engines"
 /bin/bash ./libtool   --mode=install /usr/bin/install -c  'libaurora.la' '/usr/lib/gtk-2.0/2.10.0/engines/libaurora.la'
/usr/bin/install -c .libs/libaurora.so /usr/lib/gtk-2.0/2.10.0/engines/libaurora.so
/usr/bin/install: cannot create regular file `/usr/lib/gtk-2.0/2.10.0/engines/libaurora.so': Permission denied
make[1]: *** [install-engineLTLIBRARIES] Error 1
make[1]: Leaving directory `/home/renee/GTK stuff/ENGINES/56438-aurora-1.5.1/aurora-1.5'
make: *** [install-am] Error 2

...I can't figure out what this means. Am I missing a package, or did I do the commands wrong?

---

### Post by alexdavid on 2010-05-07
hi guys,..
  i am new in this forum,..
  i found that it is very helpful for me because it contains very informative posts and sharing s,..thanks

---

### Post by dino99 on 2010-05-07
welcome

---

### Post by arnolda220 on 2010-06-26
I tried it on my *test* CentOS-5 system and was able to compile gimp  2.4.  However, it was not a "clean" installation as planned, but rather a  quick and dirty solution.  This is because some packages needed a newer  version than what is available from CentOS and I installed them from  fc6 thus overwriting the distro files.  I am going to find out if  anything on the system is broken due to this action.  Just for anyone's  info, here is a list of packages that are updated by fc6 rpm's

---

