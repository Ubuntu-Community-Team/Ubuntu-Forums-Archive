---
title: "Trying to install apache 1.3"
date: 2006-09-08
forum: Installation &amp; Upgrades
---

### Post by wilsonisme on 2006-09-08
So I tried apache 2 but I didnt like all the new changes.. Couldnt even find where to change my DocumentRoot location. This is a fresh server only install of Ubuntu. I could install apache2 with:

sudo apt-get install apache2

Like I said I have since removed apache2.

When I try to install apache 1.3, with:

sudo apt-get install apache 

I get "Package apache isn ot available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source"

So, did they remove 1.3 from the repository, rename it, or what? I want my apache 1.3! :(

On a side note, what did they change DocumentRoot too in apache2? I searched for it in pico and couldnt find it.

Thanks!

---

### Post by wilsonisme on 2006-09-09
Any insight?

---

### Post by pod25 on 2006-09-09
I'm still a newbie myself.
However if you have the server version, have you installed the GUI over the top ? and have you installed webmin to manage your server ?

---

### Post by wilsonisme on 2006-09-09
This is a server install. No XServer. Doing this the console only

---

### Post by pod25 on 2006-09-09
Well I found installing the gui then using webmin made life soooo  much easier. 
Using webmin allowed me to change my web root directory, along with just about everything else with ease.

---

### Post by xdefconx on 2008-01-02
> **pod25 said:**
> Well I found installing the gui then using webmin made life soooo  much easier. 
Using webmin allowed me to change my web root directory, along with just about everything else with ease.

Hye! I also looking for this solution which i want to install Apache 1.3.* on my Ubuntu. May i know what a name of that GUI package/where to install like u said. Since u experience with Webmin may i ask u some question:

a-Webmin did NOT come with Apache Web Server, it only come with "addon tool" to manage Apache right?

b-If yes so that mean i must install Apache first then Webmin to manage it right?

---

