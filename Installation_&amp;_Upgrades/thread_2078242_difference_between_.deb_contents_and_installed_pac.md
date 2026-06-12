---
title: "difference between .deb contents and installed package"
date: 2012-10-30
forum: Installation &amp; Upgrades
---

### Post by mrfricks on 2012-10-30
hi,

i have a question about how ubuntu installs python packages.  if i install for example 'openshot' ,  i get amongst other things,  an openshot folder in /usr/lib/pymodules.    

however, if i just undeb the openshot package and look inside, i don't see anything in /usr/lib/modules.

so what happens when ubuntu installs the openshot package?  is there a parse script that adds the extra files?  

cheers

---

### Post by Frogs Hair on 2012-10-30
This would be a good starting point.```
man dpkg
```

---

### Post by mrfricks on 2012-10-31
unzipping the .deb in ubuntu i now see the parse script thanks

---

