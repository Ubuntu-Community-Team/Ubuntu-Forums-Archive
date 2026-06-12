---
title: "Unable to get apache web server to run scripts"
date: 2011-08-11
forum: Installation &amp; Upgrades
---

### Post by redss on 2011-08-11
I've tried on both 10.04 and 10.10.  I apt-get install apache2, and put a simple "hello world" perl script in /usr/lib/cgi-bin, but when calling the script via the webserver I get a 404 "file not found" error.  

/etc/apache2/sites-available/default already contained (out of the box) 
```
ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
```

This used to work out of the box in the days of the older monolithic apache. What configuration has to be made to enable scripts to run?

---

### Post by wojox on 2011-08-11
This may still work [Install cgi on Ubuntu Server ]("http://ubuntuforums.org/showpost.php?p=8071842&postcount=2").

Good luck. :P

---

