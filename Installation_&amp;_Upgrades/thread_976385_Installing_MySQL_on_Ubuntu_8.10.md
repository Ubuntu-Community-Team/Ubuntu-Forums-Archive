---
title: "Installing MySQL on Ubuntu 8.10"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by eweibust on 2008-11-09
I want to install the mysql server on my new Ubuntu 8.10 install.  The question I have is which mysql server?  When I type sudo apt-get install mysql-server and do tab completion I see 3 mysql server options:

mysql-server      mysql-server-4.1  mysql-server-5.0  

I also see a mysql-community-server-5.0.  So I guess my first question is what is the diff between the community version and the others and then what is the story between the 3 non-community versions?  Obviously, 4.1 and 5.0 are easy but the non-version one?

thanks...
Erik

---

### Post by ilantal on 2008-11-10
Why don't you get it from the repository?

---

### Post by ShakataGaNai on 2008-12-02
Not sure about mysql-community-server since the regular versions are the community versions (versus the enterprise version).  mysql-server generally is just an alias to the latest version.  

So which do you want to install?  mysql-server-5.0

Unless you have a special reason to use an older version (compatibility with an old app, for ex).

---

### Post by arturoguedez on 2009-04-07
Hi,

I just did a fresh install of Ubuntu 8.10 64 bit on a Lenovo SL3000. Everything was going smoothly until I notices I was unable to some basic packages from the repository.

In which repository would I be able to find mysql related packages (server, client, etc) ?

Thanks

Arturo

---

### Post by snova on 2009-04-07
> **arturoguedez said:**
> I just did a fresh install of Ubuntu 8.10 64 bit on a Lenovo SL3000. Everything was going smoothly until I notices I was unable to some basic packages from the repository.

In which repository would I be able to find mysql related packages (server, client, etc) ?

They should be in main. What errors are you getting?

---

