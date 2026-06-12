---
title: "lifeograph installing trouble"
date: 2010-11-13
forum: Installation &amp; Upgrades
---

### Post by coasat on 2010-11-13
Hi,

I'm having trouble installing lifeograph. 
The following methods didn't work

- sudo apt-get install lifeograph
- "make" and "make install"  (after downloading version 0.6.3 and while in the directory)

The read me file says that I need to build the the following modules:

    * gtkmm,
    * gconfmm,
    * gtkspell, and
    * gcrypt.

Does anyone know how I can do this?

Running Xubuntu ver. 9.04 (Yes, I know I should upgrade)

Thanks,

coa

---

### Post by coasat on 2010-11-14
When I check package manager I find that these are installed (gtkmm, gconfmm, gtkspell  and gcrypt) However  when I cd to the directory 
and 'make' I get the following errors
amongst a raft of others :

g++ -c main.cpp -Wall `pkg-config gtkmm-2.4 gconfmm-2.6 gtkspell-2.0 --cflags` -O2  -o ../obj/main.o
Package gtkspell-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtkspell-2.0.pc'
to the PKG_CONFIG_PATH environment variable

How can I add the path to the environment variable?

Thanks,

---

