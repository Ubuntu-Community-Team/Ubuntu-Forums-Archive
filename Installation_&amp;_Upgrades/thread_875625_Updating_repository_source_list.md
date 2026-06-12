---
title: "Updating repository source list"
date: 2008-07-31
forum: Installation &amp; Upgrades
---

### Post by dileepm on 2008-07-31
Hi,I have ubuntu installed in my PC the problem is it has no internet connection and i have to download all the supporting libraries(debian packages) from ubuntu package site.Now that instead of installing each package manually i want to update it from a local repository... So i placed them in a separate directory and added its path to source.list in /etc/apt as "deb /Ubuntu_Local_Repositories hardy-security restricted" but when i run apt-get update i get an error that the source.list file could not be read as there is error at the line where i placed (deb /Ubuntu_Local_Repositories ....). Hope any one could help me. Quite a long question :-?

---

### Post by forger on 2008-07-31
You'll have to add the Packages file and stick a "file:" in front of the deb line in /etc/apt/sources.list
This looks like what you need:
[http://taufanlubis.wordpress.com/2007/08/15/how-to-make-local-repository-in-ubuntu/](http://taufanlubis.wordpress.com/2007/08/15/how-to-make-local-repository-in-ubuntu/)

By the way, you might want to look at apt-proxy and apt-mirror applications :)

---

