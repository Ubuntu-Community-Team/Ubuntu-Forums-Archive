---
title: "Permission denied why?"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by manojap on 2010-05-22
When I tried to install M4 package from binary I got this message


[INDENT]make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/tmp/m4-1.4.14/lib'
make[3]: Leaving directory `/tmp/m4-1.4.14/lib'
make[2]: Leaving directory `/tmp/m4-1.4.14/lib'
Making install in src
make[2]: Entering directory `/tmp/m4-1.4.14/src'
make[3]: Entering directory `/tmp/m4-1.4.14/src'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c m4 '/usr/local/bin'
/usr/bin/install: cannot create regular file `/usr/local/bin/m4': Permission denied
make[3]: *** [install-binPROGRAMS] Error 1
make[3]: Leaving directory `/tmp/m4-1.4.14/src'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/tmp/m4-1.4.14/src'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/tmp/m4-1.4.14'
make: *** [install] Error 2
manoj@manoj-desktop:/tmp/m4-1.4.14$ [/INDENT]


Please help me to solve the issue

---

### Post by dino99 on 2010-05-22
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

---

### Post by manojap on 2010-05-22
/usr/bin/install: cannot create regular file `/usr/local/bin/m4': Permission denid


why this happend?
Is there any problem with login privilage?

---

### Post by Silent Warrior on 2010-05-23
That's one of Linux's many security features. You normally aren't allowed to install anything unless you're the administrator. It'll probably serve you better to read through the help-site dino posted a link to than having mere myself trying to explain it. One clue for you, though, to give you a starting-point: sudo.

(Oh, and just so you know, what you're trying to do is called installing from **source**, not binary. You get binaries through Synaptic/Software Central/apt-get. Unless you have a very good reason to compile m4 from source, use those instead.)

---

