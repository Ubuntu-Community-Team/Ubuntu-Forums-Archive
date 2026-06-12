---
title: "Compiling .tar.gz MailReactor source"
date: 2011-05-20
forum: Installation &amp; Upgrades
---

### Post by geidorei on 2011-05-20
Hi having some issues here - trying to install MailRector

extracted etc - type in make and it says:

c++ -I../fltk-1.0.6 -O2 -c MailReact.cxx
In file included from MailReact.cxx:4:0:
sfl.h:229:80: fatal error: iostream.h: No such file or directory
compilation terminated.
make: *** [MailReact.o] Error 1

Any ideas folks???????

Thanks, Karl

---

### Post by geidorei on 2011-05-20
Follow up to thsi - in case it was me, tried to install another .tar.gz called watsup - this is what i got

g++ -O3 -g -Wall -c `pkg-config --cflags gtk+-2.0` -o watsup.o watsup-1.9.cc
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
In file included from watsup-1.9.cc:27:0:
zfuncs.h:257:21: fatal error: gtk/gtk.h: No such file or directory
compilation terminated.
make: *** [watsup.o] Error 1

gtk+-2.0 is installed

Whats going on, more to the point what do I need to do???? ahhhhh!

Karl

---

### Post by geidorei on 2011-05-20
...and after more investigation - according to ubuntu docs i should try running ./configure - configure does not exist, not can I apt-get it.

---

### Post by oldos2er on 2011-05-20
Is this it? [http://www.daansystems.com/mailreactor/](http://www.daansystems.com/mailreactor/)
That's a very old program, if I were you I'd look in the repositories for something a little more up-to-date.

> sfl.h:229:80: fatal error: iostream.h: No such file or directory**apt-cache search iostream** shows several packages; libpstreams-dev looks like it might be the one you need.

> No package 'gtk+-2.0' foundDo you have libgtk2.0-dev installed? 

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by geidorei on 2011-05-20
Hi Thanks for info.

Installed  libpstreams-dev and libgtk2.0-dev - no luck, same error. 

Why is installing tar.gz programs so piggin difficult??????

---

### Post by geidorei on 2011-05-20
right then, think now sorted.

I sorta cheated here, pulled down the dropbox.tar.gz - as dropbox is available via a .deb i assumed that their tar.gz would be aok. I was right.

ran ./configure and it told me to install (did via synaptic) - python-docutils and libnautilus-extension- dev

re-ran ./configure all aok, then make - and it worked.

All I can say is that sometimes its really hard work with linux. But I aint going back to windows, thats for sure.

---

### Post by geidorei on 2011-05-20
ok i tell a lie - too early.

Managed to get watsup to work but no chance with MailRecator.

bugger!

---

### Post by geidorei on 2011-05-20
as anote, again this is what it says on trying to make MailReactor:

c++ -I../fltk-1.0.6 -O2 -c MailReact.cxx
In file included from MailReact.cxx:4:0:
sfl.h:229:80: fatal error: iostream.h: No such file or directory
compilation terminated.
make: *** [MailReact.o] Error 1

---

### Post by oldos2er on 2011-05-20
> **geidorei said:**
> Hi Thanks for info.

Installed  libpstreams-dev and libgtk2.0-dev - no luck, same error. 

Why is installing tar.gz programs so piggin difficult??????

You're trying to compile 12 year old code. Many things have changed in that time.

---

### Post by geidorei on 2011-05-22
Hi ummm. yes i realise now, why has this person still got this avilable to download??? ummmm

---

