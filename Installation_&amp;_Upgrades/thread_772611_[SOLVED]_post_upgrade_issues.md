---
title: "[SOLVED] post upgrade issues"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by sorak on 2008-04-28
upgraded from 7.10 to 8.04... mostly smooth... mostly expected issues, had to reinstall video and wireless drivers. not sure on these, though...

---

nautilus fails to execute with the following error:

nautilus: symbol lookup error: nautilus: undefined symbol: g_file_query_filesystem_info_async

the only page i could find that listed this error was in a language i dont recognize.

----

epiphany crashes just after loading the gui with the following error:

epiphany-browser: symbol lookup error: epiphany-browser: undefined symbol: g_uri_parse_scheme

i found a bug report concerning this here:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=470473](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=470473)

---

anybody? :)

---

### Post by yyyc186 on 2008-04-28
Go back to 7.10.  Wait until at least 8.10 before trying again.

---

### Post by sorak on 2008-04-28
uhm, i dont know about you, but thats not how i solve problems. a couple of unresolved symbol issues is no reason to downgrade. there may be a couple of libraries that need to be downgraded, but certainly not the entire system.

---

### Post by sorak on 2008-06-26
bump

---

### Post by sorak on 2008-06-27
nobody seems to care, but i fixed it by installing glib-2.15.6 manually (it isnt in apt)

---

