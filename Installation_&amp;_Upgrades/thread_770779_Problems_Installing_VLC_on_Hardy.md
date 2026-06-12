---
title: "Problems Installing VLC on Hardy"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by gatepc on 2008-04-27
I'm trying to install VLC on my Ubuntu 8.04, so I tried going into Add/Remove Programs and installing it there, but I get the following error:

[B]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/B]

So I tried going to their official site and installing it, but I get the same error.

Oh, and by the way, I tried entering **dpkg --configure -a** in the terminal, but then i get the error:

**dpkg: requested operation requires superuser privilege**

---

### Post by oldos2er on 2008-04-27
Run "sudo dpkg --configure -a"

---

### Post by gatepc on 2008-04-27
Now it's constantly looping:

[B]^
/var/lib/scrollkeeper/C/scrollkeeper_cl.xml:1: parser error : Start tag expected, '<' not found

^
/var/lib/scrollkeeper/C/scrollkeeper_cl.xml:1: parser error : Document is empty[/B]

---

### Post by gatepc on 2008-04-27
Nevermind, I got it fixed.

---

