---
title: "Missing Install LAMP option"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by Kimos on 2006-10-26
Should be a simple question...

I keep reading about the "Install LAMP" option for the Server installation CD in 6.10 (and also 6.06), but for some reason it's just missing. Tried it on two machines...

When I boot my screen looks just like it does in the *first* step of this guide, except I only have five options instead of six:
[http://www.howtoforge.com/node/1388]("http://www.howtoforge.com/node/1388")

I've read about a few people who have encountered this, but never anyone who can explain it (or fix it :P).

Thanks!

---

### Post by Kimos on 2006-10-26
Found this:
[http://www.ubuntuforums.org/archive/index.php/t-187673.html](http://www.ubuntuforums.org/archive/index.php/t-187673.html)

Does this mean that it's still not implemented because of hardware limitations? That seems a little strange.

---

### Post by az on 2006-10-26
> **Kimos said:**
> 
I've read about a few people who have encountered this, but never anyone who can explain it (or fix it :P).

Thanks!

Exactly what cd do you have?  Is it the final cd?  The LAMP stack should run on any architecture - it does not involve any special arcitecture.

Anyhow, even if you install just a base system, you can install the LAMP stack by running

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

and you will end up with exactly the same thing had you installed using the LAMP option.

Weird.

---

### Post by arosenau on 2006-10-26
In the 6.10 cd the option was simply removed from the main bootup menu. If you simply choose "Install Server" after it installs the base system it will ask you if you want to install a LAMP server and will also give you the option of installing a DNS server. Alternitivly if you already have it installed you can follow the guide here to install everything you need.

[http://www.howtoforge.com/perfect_setup_ubuntu_6.10]("http://www.howtoforge.com/perfect_setup_ubuntu_6.10")

---

### Post by Kimos on 2006-10-26
> Exactly what cd do you have? Is it the final cd?
It's 6.10 server final I torrented this morning.

> If you simply choose "Install Server" after it installs the base system it will ask you if you want to install a LAMP server
Ok cool. Never got that far cause my HD failed, but I'll look for that.

I know there were other ways of doing it, but the whole 15 min LAMP thing seemed exciting, and I had *no* idea why my CD would be different from what everyone else seems to have.

Cheers. Thanks for the help!

---

