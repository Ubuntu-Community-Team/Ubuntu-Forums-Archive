---
title: "problem with ioncube loader"
date: 2011-11-22
forum: Installation &amp; Upgrades
---

### Post by mzh14 on 2011-11-22
[LEFT]hi
i install php and mysql and ioncube loader to run encoding 
but it is not working 
i didnt see any thing about ioncube when i write phpinfo()
i add this line to php.ini

zend_extension = /usr/local/lib/ioncube/ioncube_loader_lin_5.3.so

but still not working

can any body help me?
[/LEFT]

---

### Post by mzh14 on 2011-11-23
nobody can help me???

---

### Post by raja.genupula on 2011-11-23
> **mzh14 said:**
> [LEFT]hi
i install php and mysql and ioncube loader to run encoding 
but it is not working 
i didnt see any thing about ioncube when i write phpinfo()
i add this line to php.ini

zend_extension = /usr/local/lib/ioncube/ioncube_loader_lin_5.3.so

but still not working

can any body help me?
[/LEFT]

I think you have to mention Quotes for that extension 
i  mean zend_extension="/usr/local/lib/ioncube/ioncube_loader_lin_5.3.so"

and then restart apache 
```
sudo /etc/init.d/apache2 restart
```
let me know what you got.

---

