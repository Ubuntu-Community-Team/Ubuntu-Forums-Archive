---
title: "problems with Tar.gz compillation"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by cool_connor on 2010-01-29
hello...
it's my second post in this forum, and...my new problem is this...

i downloaded a plasmoid from internet ...
this comes in a tar.gz (no ready packages in the web)
and i don't know how compile it...
./configure doesn't work

the tar.gz comes with a "setup.txt" ...

in wich can reads "Installation
============

First, you need a complete build environment. You must install packages cmake, make, gcc, g++, gettext and
KDE development packages. These packages are called differently, depending on your distribution:
kde-devel on Ubuntu, task-kde4-devel on Mandriva, or similar.

mkdir build
cd build
cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` ..
make
make install
kbuildsycoca4"


but i dont understand how make it... i can do the 2 first steps only
when i put the third step
it givemes an error



"Configurando gettext (0.17-8ubuntu2) ...

Procesando disparadores para libc-bin ...
ldconfig deferred processing now taking place
adrian@ubuntu:~/Documentos/plasma-widget-cwp-0.9.15~jaunty~ppa1/build$ cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` ..
CMake Error at /usr/share/cmake-2.6/Modules/FindKDE4.cmake:84 (MESSAGE):
  ERROR: cmake/modules/FindKDE4Internal.cmake not found in
  /home/adrian/.kde/share/apps;/usr/share/kubuntu-default-settings/kde4-profile/default/share/apps;/usr/share/kde4/apps
Call Stack (most recent call first):
  CMakeLists.txt:5 (find_package)


-- Configuring incomplete, errors occurred!
"


thanks in advance.

---

### Post by cool_connor on 2010-01-30
Bump!...
someone will help me?

---

