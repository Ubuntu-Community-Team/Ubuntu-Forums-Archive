---
title: "Installation: Setting up proxy?"
date: 2005-02-17
forum: Installation &amp; Upgrades
---

### Post by Zenith on 2005-02-17
Just a suggestion, or perhaps a question  :wink: 

Upon installing Ubunty, it at some points asks if you want to use online repositories for updating your software, and if you answers "yes", it will immediately try to connect to the repository.
Shouldn't there be some way of specifying a proxy beforehand? It sort of bugs me that I have to drop to a shell first or say no to be able to get this working during the install.

Any solutions or perhaps a feature request instead?

---

### Post by cyberchills on 2005-02-17
Same here.   Good point

For others viewing this post a quick workaround is to do the following:

1. answer no and finish install
2. setup proxy variables 
http_proxy="http://whateveryproxy.com:80"  
ftp_proxy="http://whateveryproxy.com:80"

Note: Change your port address to reflect the correct one 80, 8080 1080, etc..
the second example proxies ftp through a http tunnel, don't know if I ever need it.

Then do your apt-get update

---

### Post by Zenith on 2005-03-05
Last I tried no such option had been made, is there talks about this or what? Seems like an error to me, as many people potentially could be behind a proxy during their installs...

---

### Post by brolewis on 2005-04-01
Where do I need to set those variables? I am behind a firewall and unable to get apt-get to work :(

---

