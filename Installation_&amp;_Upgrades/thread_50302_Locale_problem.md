---
title: "Locale problem"
date: 2005-07-19
forum: Installation &amp; Upgrades
---

### Post by fnando on 2005-07-19
I'm using an english version of ubuntu setted as pt_br iso8859-1 locale.

The problem is that when I access pages with accents (áéíóú.....) I see some strange characters. I attached one image to show this issue.

The locale command returns this:

> LANG=pt_BR
LC_CTYPE="pt_BR"
LC_NUMERIC="pt_BR"
LC_TIME="pt_BR"
LC_COLLATE="pt_BR"
LC_MONETARY="pt_BR"
LC_MESSAGES="pt_BR"
LC_PAPER="pt_BR"
LC_NAME="pt_BR"
LC_ADDRESS="pt_BR"
LC_TELEPHONE="pt_BR"
LC_MEASUREMENT="pt_BR"
LC_IDENTIFICATION="pt_BR"
LC_ALL=

Running locale -a I get this:

> C
POSIX
pt_BR
pt_BR.iso88591

I noticed that when I use firefox, it changes to Unicode UTF-8 by itselft.


So, how to solve this?

---

