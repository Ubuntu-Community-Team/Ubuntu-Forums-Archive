---
title: "couldn't find package dhcpd"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by hanserikbusk on 2007-06-04
kubuntu server 6.06 dapper.
I want to install a dhcp-server, but get the response in the title when I write:
sudo apt-get install dhcpd.
with a 

I have 
... dapper main restricted
... dapper-updates main restricted
... dapper-security main restricted

in my sources.list

Several other packages (apache, subversion ) has installed without problems. I am quite new to the debian way, coming from SuSE. 
So I am a bit lost though the apt-get system seems more smooth than Yast.

What to do now ?
:-s

---

### Post by zvacet on 2007-06-04
[http://doc.ubuntu.com/ubuntu/serverguide/C/extra-repositories.html]("http://doc.ubuntu.com/ubuntu/serverguide/C/extra-repositories.html")

---

### Post by hanserikbusk on 2007-06-04
> **zvacet said:**
> [http://doc.ubuntu.com/ubuntu/serverguide/C/extra-repositories.html]("http://doc.ubuntu.com/ubuntu/serverguide/C/extra-repositories.html")

Thank you very much. Now I got a successfull installation.
Just wondering why dhcpd isn't in the restricted repository.
:p

---

