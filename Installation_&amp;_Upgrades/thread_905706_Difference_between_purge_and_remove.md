---
title: "Difference between purge and remove ?"
date: 2008-08-30
forum: Installation &amp; Upgrades
---

### Post by akwatve on 2008-08-30
Hi,

This may not be so important. But I want to know the difference between "purging" a package and "removing" it. This is with reference to adept-manager in particular.

thanks,

---

### Post by loboc on 2008-08-30
remove deletes the application and some of the associated files

Purge removes everything related like configuration scripts and what not

remover leaves stuff so if you say remove and then reinstall samba your shares are still configured

---

### Post by forger on 2008-08-30
first hit: [http://www.google.com/search?q=difference+remove+and+purge](http://www.google.com/search?q=difference+remove+and+purge)
[http://ubuntuforums.org/showpost.php?p=2312269&postcount=3](http://ubuntuforums.org/showpost.php?p=2312269&postcount=3)
> 
purge also removes any configuration files, while remove removes the software but no configuration files (AFAIK). So if you want to start out fresh, you probably want to purge things.

---

