---
title: "gtk+2 install problem"
date: 2005-06-17
forum: Installation &amp; Upgrades
---

### Post by BabyUbuntu on 2005-06-17
hello ubuntu

i tried to installed gtk+2 but i got problem ...

root@babyubuntu:/home/babyubuntu/Mydocument/gtk+-2.0.3 #./configure --prefix=/usr

---- compile process ---

checking for freetype-config... /usr/local/bin/freetype-config
checking for FT_New_Face in -lfreetype... yes
checking For sufficiently new FreeType (at least 2.0.1)... no
configure: error: pangoxft Pango backend found but did not find freetype libraries

root@babyubuntu:/home/babyubuntu/Mydocument/gtk+-2.0.3#

c[B]onfigure: error: pangoxft Pango backend found but did not find freetype libraries

[/B] <-- i thougt i have to install pangocft ... then i asked it to mr google and mr sourceforge... i got this file freetype-2.1.8.. than i tried to install it


root@babyubuntu:/home/babyubuntu/Mydocument/freetype-2.1.8 # ./configure --prefix=/usr/

FreeType build system -- automatic system detection

The following settings are used:

  platform                    unix
  compiler                    cc
  configuration directory     ./builds/unix
  configuration rules         ./builds/unix/unix.mk

If this does not correspond to your system or settings please remove the file
`config.mk' from this directory then read the INSTALL file for help.

Otherwise, simply type `make' again to build the library,
or `make refdoc' to build the API reference (the latter needs python).

make: Nothing to be done for `unix'.
root@babyubuntu:/home/babyubuntu/Mydocument/freetype-2.1.8 #

i asked mr google and sourceforge again how to install freetype-2.1.8 .. and they said same answer ..

./configure
make
make install

without problem like mine..  any solution for my problem , help pls.

thank u very much

---

### Post by DJ_Max on 2005-06-20
Why are you trying to install GTK+, it should already be installed, if not, just apt-get it? 

You have to finish installing freetype, which you didn't. Listen to what whoever told you to ./configure, make, make install.

```

./configure --prefix=/usr/
make
sudo make install

```

---

