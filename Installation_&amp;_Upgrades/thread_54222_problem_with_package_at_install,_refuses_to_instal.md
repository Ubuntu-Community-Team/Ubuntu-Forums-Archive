---
title: "problem with package at install, refuses to install"
date: 2005-08-03
forum: Installation &amp; Upgrades
---

### Post by Jessehk on 2005-08-03
Okay, at initial install, Ubuntu told me it had problems with 

librdf0 and librasqal10 because the were dependent on libraptor1

Therefore, it sent me to aptitude, where I tried to install libraptor1. It wouldn't let me. 

Giving up ( after spending about 15 minutes on it ), I quit aptitude, and continued with the installation. 

Everything works, as these seem to be just programming libraries, but I don't want broken packages on an initial install. It doesn't give a good first impression ( if you know what I mean.  :) )

When I try to install libraptor1 with synaptic, I see the following message:

[http://images5.theimagehosting.com/Screenshot-Error.png](http://images5.theimagehosting.com/Screenshot-Error.png)
What do I do?

thanks

---

### Post by Jessehk on 2005-08-03
[QUOTE=Jessehk]Okay, at initial install, Ubuntu told me it had problems with 

librdf0 and librasqal10 because the were dependent on libraptor1

Therefore, it sent me to aptitude, where I tried to install libraptor1. It wouldn't let me. 

Giving up ( after spending about 15 minutes on it ), I quit aptitude, and continued with the installation. 

Everything works, as these seem to be just programming libraries, but I don't want broken packages on an initial install. It doesn't give a good first impression ( if you know what I mean.  :) )

When I try to install libraptor1 with synaptic, I see the following message:

[http://images5.theimagehosting.com/Screenshot-Error.png](http://images5.theimagehosting.com/Screenshot-Error.png)
What do I do?

thanks[/QUOTE]
 I apologise, this belongs in 5.04, not 4.10.

please have it moved.

---

### Post by az on 2005-08-04
Try running the command

sudo dpkg --clear-avail

sudo apt-get -f install

Perhaps that will help.

---

