---
title: "Distr-upgrade Edgy to Feisty problems."
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by disoul on 2007-08-14
I recently upgraded my Edgy eft to Feisty Fawn with the 'update-manager', and now I'm with seriously problems.
My aptitude is in pt-BR, but I'm translating:

# apt-get upgrade

Installing mono-common (1.2.3.1-1ubuntu1) ...
dpkg: error processing mono-common (--configure):
fail in buffer_read(fd): md5hash: Input/output error
dpkg: dependency problems stop mono-jit installation:
 mono-jit depends mono-common (= 1.2.3.1-1ubuntu1); but:
  Package mono-common isn't configured yet.
dpkg: error processing mono-jit (--configure)..

(and a lot of packages with dependency errors:)
 mono-common
 mono-jit
 libmono-corlib1.0-cil
 mono-gac
 mono-runtime
 libmono-system1.0-cil
 libglib2.0-cil
 libgconf2.0-cil
 libmono-cairo1.0-cil
 libgtk2.0-cil
 libglade2.0-cil
 libgnome2.0-cil
 libmono-corlib2.0-cil
 libmono-system2.0-cil
 libmono-security2.0-cil
 libmono-sharpzip2.84-cil
 libmono-data-tds2.0-cil
 libmono-system-data2.0-cil
 libmono-sqlite2.0-cil
 libmono-system-web2.0-cil
 libmono2.0-cil
 libndesk-dbus1.0-cil
 libndesk-dbus-glib1.0-cil
 f-spot


By the way,  I did read a topic here with same error, but in 'imake', and a simply dpkg -i imake*.deb solved the problem.


# dpkg -i mono-common*.deb
(Reading database... 106894 files and directories installed)

Preparing to replace mono-common 1.2.3.1-1ubuntu1 (using mono-common_1.2.3.1-1ubuntu1_i386.deb) ...

Descompressing mono-common ...
Installing mono-common (1.2.3.1-1ubuntu1) ...
dpkg: error processing mono-common (--install):
fail in buffer_read(fd): md5hash: Input/output error.


I really don't know what I can do, I did try download again the .deb file and dpkg, but I got the same error.

---

### Post by disoul on 2007-08-14
Ok, it's a problem, but my xorg still running =D

do you have an idea about the mono-common install and the dependencies?

I'm waiting, thank you at moment =)

---

