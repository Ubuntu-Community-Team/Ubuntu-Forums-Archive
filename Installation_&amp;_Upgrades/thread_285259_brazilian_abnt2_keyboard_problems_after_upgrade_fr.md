---
title: "brazilian abnt2 keyboard problems after upgrade from dapper to edgy"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by streeto on 2006-10-26
My keyboard model is Brazilian abnt2. In dapper every key was working. After upgrading to edgy, the (/,?,°) key does not work in console anymore. Also, in rxvt, the accents aren't dead keys so I can't type ã,é,etc. In emacs, the accent keys beep and don't print ~,',etc, neither work as dead keys. Gtk based apps work just fine.

I found this bug, but it appears to be resolved, and not related to my problem.

[https://launchpad.net/distros/ubuntu/+source/console-setup/+bug/66774](https://launchpad.net/distros/ubuntu/+source/console-setup/+bug/66774)

Anyone with a abnt2 keyboard have this problem?

---

### Post by gian.ricardo on 2006-10-27
hi,

i am facing the same problem. Does anyone know how to fix it?

thanks

---

### Post by neymac on 2006-10-27
+1

---

### Post by asfonseca on 2006-10-30
> **streeto said:**
> My keyboard model is Brazilian abnt2. In dapper every key was working. After upgrading to edgy, the (/,?,°) key does not work in console anymore. Also, in rxvt, the accents aren't dead keys so I can't type ã,é,etc. In emacs, the accent keys beep and don't print ~,',etc, neither work as dead keys. Gtk based apps work just fine.

I found this bug, but it appears to be resolved, and not related to my problem.

[https://launchpad.net/distros/ubuntu/+source/console-setup/+bug/66774](https://launchpad.net/distros/ubuntu/+source/console-setup/+bug/66774)

Anyone with a abnt2 keyboard have this problem?

Yeap, me too!

---

### Post by streeto on 2006-10-31
I would like to add that every KDE/Qt programs presentes the deadkeys problem. Tested it here (for some KDE programs installed, kate and k3b for instance) and confirmed. Found this discussion:

[http://www.mail-archive.com/debian-qt-kde@lists.debian.org/msg16589.html](http://www.mail-archive.com/debian-qt-kde@lists.debian.org/msg16589.html)

It seems there's a bug in xkb-data.

---

### Post by streeto on 2006-11-09
I think I found the solution. The locale here was set to pt_BR.ISO-8859-1 (latin-1). Changing to pt_BR.UTF-8 resolved the accents (dead keys) problem with KDE-based programs and emacs.

sudo dpkg-reconfigure localeconf

then select pt_BR.UTF-8.

But now, the accents in my latin-1 files look like garbage, when I open them in a xterm. I will try to find a way to correct this.

Looks like devs. are trying to drive people from the latin-1 world to utf-8 world. :-?

---

### Post by streeto on 2006-11-10
OK, now I got everything right. 8)

I installed rxvt-unicode and updated the x-terminal-emulator alternative:

sudo aptitude install rxvt-unicode-lite
sudo update-alternatives --config x-terminal-emulator (select urxvt)

By the way, UTF-8 is not that bad. I thought I would have to convert all my latin-1 files to UTF-8, but emacs handles them just fine. :-D

---

### Post by pedrorolo on 2006-11-30
oi! Aqui do outro lado do Atlantico estou com o mesmo problema. Fiz como fizeste, mas nada funciona na mesma. 

Como consigo ver qual o meu locale actual?

Eu faço "pessoa@computador~ $ locale" mas apenas me é listado "pt_PT", não dizendo nada relativo ao encoding.

Para que é essa linha do urxvt?!

---

### Post by Rhaurison Bergamin on 2006-12-14
Have you run dpkg-reconfigure localeconf as streeto said ?
PS. check all variables when asked for "what should locales control" AND choose "Yes" for "debconf control locales files".

---

