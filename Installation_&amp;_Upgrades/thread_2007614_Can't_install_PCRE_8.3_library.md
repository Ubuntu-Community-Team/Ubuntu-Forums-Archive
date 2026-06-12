---
title: "Can't install PCRE 8.3 library"
date: 2012-06-21
forum: Installation &amp; Upgrades
---

### Post by Odolyte on 2012-06-21
Hi,

I can't install the PCRE 8.3 library.

i Followed what was mentioned in that post :
[http://ubuntuforums.org/showthread.php?p=12041475#post12041475](http://ubuntuforums.org/showthread.php?p=12041475#post12041475)

First, i didn't have a compiler so i installed gcc-c++ as suggested @soungcha.

./configure went ok.
when typing "make" i have this message now :

Code:
```
rm -f pcre_chartables.c
ln -s ./pcre_chartables.c.dist pcre_chartables.c
make  all-am
make[1]: entrant dans le répertoire « /usr/local/src/pcre-8.30 »
  CC     pcre_byte_order.lo
  CC     pcre_compile.lo
  CC     pcre_config.lo
  CC     pcre_dfa_exec.lo
  CC     pcre_exec.lo
  CC     pcre_fullinfo.lo
  CC     pcre_get.lo
  CC     pcre_globals.lo
  CC     pcre_jit_compile.lo
  CC     pcre_maketables.lo
  CC     pcre_newline.lo
  CC     pcre_ord2utf8.lo
  CC     pcre_refcount.lo
  CC     pcre_string_utils.lo
  CC     pcre_study.lo
  CC     pcre_tables.lo
  CC     pcre_ucd.lo
  CC     pcre_valid_utf8.lo
  CC     pcre_version.lo
  CC     pcre_xclass.lo
  CC     pcre_chartables.lo
  CCLD   libpcre.la
  CC     pcreposix.lo
  CCLD   libpcreposix.la
  CXX    pcrecpp.lo
libtool: compile: unrecognized option `-DHAVE_CONFIG_H'
libtool: compile: Try `libtool --help' for more information.
make[1]: *** [pcrecpp.lo] Error 1
make[1]: leaving folder « /usr/local/src/pcre-8.30 »
make: *** [all] Error 2
```

Sorry for my Linux incompetence, i'm new to Linux and have a lot of things to learn...

Thx for your help!

Odo.

---

### Post by borealisUM on 2012-06-25
I am having the exact same problem. Does anybody know how to fix this? 

Thanks in advance!

---

### Post by marinara on 2012-06-26
downloaded pcre and did configure,make
worked ok

what exactly did you type to make the project?

---

### Post by borealisUM on 2012-06-26
I don't know what changed but when I logged back in today and did:

./configure
make
sudo make install

everything installed correctly and I didn't receive that error message again.  Thanks for replying so quickly though! :)

---

### Post by Incarnadin on 2013-02-03
Just wanted to say that this is exactly what happened to me. I pretty much gave up. Came back a couple days later and did the exact same thing I had been doing and it worked perfectly. Apparently, time is the fix for this problem!

---

