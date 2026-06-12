---
title: "graphviz libcairo symbol lookup error FT_Library_SetLcdFilter"
date: 2008-09-29
forum: Installation &amp; Upgrades
---

### Post by vidi on 2008-09-29
Hi,

i have installed graphviz, xampp and mediawiki1.13 on my hardy (VM).
If i'll compile graphviz manually, it is going great.
if i use /usr/bin/dot out of xampp, i do always get this error:

/usr/bin/dot: symbol lookup error: /usr/lib/libcairo.so.2: undefined symbol: FT_Library_SetLcdFilter

please help me!!!

---

### Post by cristianpark on 2010-04-29
> **vidi said:**
> Hi,

i have installed graphviz, xampp and mediawiki1.13 on my hardy (VM).
If i'll compile graphviz manually, it is going great.
if i use /usr/bin/dot out of xampp, i do always get this error:

/usr/bin/dot: symbol lookup error: /usr/lib/libcairo.so.2: undefined symbol: FT_Library_SetLcdFilter

please help me!!!Even when this issue is too old. I'll answer for everyone who has a problem like this in the future.

I have Xampp 1.7.1 and Graphviz 2.26.3 and I was getting an error like the one above when I tried to use DOT from PHP, from terminal it works ok.

I did: [PHP]ldd /usr/local/lib/graphviz/libgvplugin_pango.so.6[/PHP]from a PHP script [1] and from a terminal [2] and I found that libfreetype referenced from PHP was pointing to /opt/lampp/lib instead of /usr/lib. So the fix is to make a symlink from /usr/lib/libfreetype to /opt/lampp/lib/libfreetype
[PHP]sudo ln -s /usr/lib/libfreetype.so.6 /opt/lampp/lib/libfreetype.so.6[/PHP]

I hope this can help anyone who faces this problem again

[1] [http://pastebin.com/RcUjRGF3](http://pastebin.com/RcUjRGF3)
[2] [http://pastebin.com/EjPffaaq](http://pastebin.com/EjPffaaq)

---

### Post by Eezyville on 2011-02-10
Thank you cristianpark!

That helped me with a similar issue I was having. :D

---

