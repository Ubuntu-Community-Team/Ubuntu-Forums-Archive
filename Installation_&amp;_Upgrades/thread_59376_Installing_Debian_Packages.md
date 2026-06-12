---
title: "Installing Debian Packages"
date: 2005-08-23
forum: Installation &amp; Upgrades
---

### Post by dJnEvS on 2005-08-23
What i have read is that Ubuntu is based on debian.. ](*,) 
so, i download deb packages, but i am unable to install it correctly (not sure)
the deb files opens with File-Roller. but i cant install packages with it.. (i think)
just extract..

is there a way (like SuSE has yast) to install packages? or with a command?

Regards dJnEvS.. :)

---

### Post by amastronardi on 2005-08-23
in a terminal type:
```
sudo dpkg --install *package_file* 
```

Cheers, Adrian.

---

### Post by Rob2687 on 2005-08-23
[QUOTE=dJnEvS]What i have read is that Ubuntu is based on debian.. ](*,) 
so, i download deb packages, but i am unable to install it correctly (not sure)
the deb files opens with File-Roller. but i cant install packages with it.. (i think)
just extract..

is there a way (like SuSE has yast) to install packages? or with a command?

Regards dJnEvS.. :)[/QUOTE]
 dpkg -i nameoffile.deb

---

### Post by amastronardi on 2005-08-23
from man page:

ACTIONS
dpkg -i | --install package_file...
      Install  the  package. If  --recursive  or -R option is specified, package_file must refer to a directory instead.

-i and --install are both accepted options.

Cheers, Adrian.

---

### Post by dJnEvS on 2005-08-23
it works :D

thanks guys..


(fast responding here :D like that :) )

---

