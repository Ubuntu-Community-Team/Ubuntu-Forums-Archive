---
title: "[SOLVED] Add LAMP to Ubuntu Server the &amp;quot;right way&amp;quot;"
date: 2007-06-20
forum: Installation &amp; Upgrades
---

### Post by SDraconis on 2007-06-20
I installed Ubuntu Server 7.04, but didn't do the LAMP install initially.  Now I want to go back and do it, but I can't seem to figure out how.  I know there's the method of installing all the packages I need myself from aptitude, but that seems like it defeats the advertised idea of having a low-config LAMP install.  I also read somewheres here about configuring Synaptic to help me do the LAMP install, but that requires Synaptic (and therefore X) to be installed.

---

### Post by alanandhispc on 2007-06-20
The command to use is: 

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

this is exactly what the installer does, so it can't get easier than that.



Alan

---

### Post by az on 2007-06-20
Alternatively, since Edgy, you can run

sudo tasksel

and pick LAMP.  Again, exactly the same thing.

---

### Post by SDraconis on 2007-06-20
Thanks.  I didn't realize that the included LAMP installation task didn't do anything different than installing the packages.  I personally like tasksel.

---

### Post by aktxyz on 2007-12-03
its not really EXACTLY the same thing, the tasksel method also asks you to set a mysql root password, not sure if there is any other differences

---

