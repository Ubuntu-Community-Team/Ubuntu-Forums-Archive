---
title: "Gambas2 not installing on 8.04 on x86-64."
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by Chris_no on 2010-03-25
Hello I'm having problems installng gambas2 on 8.04.
My machine is x86-64.

sudo apt-get install gambas2

Gives me this

> 
(I'v translated this)
Reading packages ... Done
Making dependencies      
Reading state information ... Done
Some packages couldn't be installed. This might mean that you have
asked for a impossible condition or, if you use the unstable version
of Debian, that certain corepackages isn't yet made or moved out of
"incoming" for the distrubution.

Since you only made one change it is overwhelmingly probable that
the package can't be installed, and you should just fill out an error report.

The following information can be of help to solve the problem:

(Avhenger av: = Depends on)
(men lar seg ikke installere = but can't be installed)

The following packages have unmet dependencies:
  gambas2: Avhenger av: gambas2-gb-compress-bzlib2 (>= 1.9.49-1) men lar seg ikke installere
           Avhenger av: gambas2-gb-compress-zlib (>= 1.9.49-1) men lar seg ikke installere
           Avhenger av: gambas2-gb-crypt (>= 1.9.49-1) men lar seg ikke installere
           Avhenger av: gambas2-gb-db-firebird men lar seg ikke installere
           Avhenger av: gambas2-gb-db-mysql (>= 1.9.49-1) men lar seg ikke installere
           Avhenger av: gambas2-gb-db-postgresql (>= 1.9.49-1) men lar seg ikke installere
           Avhenger av: gambas2-gb-db-odbc (>= 1.9.49-1) men lar seg ikke installere
           Avhenger av: gambas2-gb-db-sqlite (>= 1.9.49-1) men lar seg ikke installere eller
                        gambas2-gb-db-sqlite2 (>= 1.9.49-1) men lar seg ikke installere
           Avhenger av: gambas2-gb-form (>= 1.9.49-1) men lar seg ikke installere
           Avhenger av: gambas2-gb-form-mdi (>= 1.9.49-1) men lar seg ikke installere
           Avhenger av: gambas2-gb-gtk (>= 1.9.49-1) men lar seg ikke installere
           Avhenger av: gambas2-gb-gtk-svg men lar seg ikke installere
           Avhenger av: gambas2-gb-image (>= 1.9.49-1) men lar seg ikke installere
           Avhenger av: gambas2-gb-info (>= 1.9.49-1) men lar seg ikke installere
           Avhenger av: gambas2-gb-ldap (>= 1.9.49-1) men lar seg ikke installere
           Avhenger av: gambas2-gb-net-curl (>= 1.9.49-1) men lar seg ikke installere
           Avhenger av: gambas2-gb-net-smtp (>= 1.9.49-1) men lar seg ikke installere
           Avhenger av: gambas2-gb-opengl (>= 1.9.49-1) men lar seg ikke installere
           Avhenger av: gambas2-gb-pcre (>= 1.9.49-1) men lar seg ikke installere
           Avhenger av: gambas2-gb-pdf (>= 1.9.49-1) men lar seg ikke installere
           Avhenger av: gambas2-gb-qt-ext (>= 1.9.49-1) men lar seg ikke installere
           Avhenger av: gambas2-gb-qt-kde-html (>= 1.9.49-1) men lar seg ikke installere
           Avhenger av: gambas2-gb-qt-opengl men lar seg ikke installere
           Avhenger av: gambas2-gb-sdl (>= 1.9.49-1) men lar seg ikke installere
           Avhenger av: gambas2-gb-settings (>= 1.9.49-1) men lar seg ikke installere
           Avhenger av: gambas2-gb-vb men lar seg ikke installere
           Avhenger av: gambas2-gb-v4l (>= 1.9.49-1) men lar seg ikke installere
           Avhenger av: gambas2-gb-web men lar seg ikke installere
           Avhenger av: gambas2-gb-xml (>= 1.9.49-1) men lar seg ikke installere
           Avhenger av: gambas2-ide (>= 1.9.49-1) men lar seg ikke installere

E: Broken packages:


Is this something to do with all the library's being i386?
Or is there some other issue at play here?

I would prefer not to install by source if it can be avoided.
Makes everything cleaner.

---

