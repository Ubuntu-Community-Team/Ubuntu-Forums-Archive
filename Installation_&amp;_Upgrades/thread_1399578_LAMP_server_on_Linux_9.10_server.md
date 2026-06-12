---
title: "LAMP server on Linux 9.10 server"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by D-rock on 2010-02-05
Hello Guys -

I've been messing around for a few days now trying to figure out what is going on and I feel like I'm making a stupid mistake.  Essentially I'm trying to build a LAMP server (PHP) on my Mac Mini using VMWare Fusion 3 using Linux Server 9.10.  To start, it's not going well at all.  Once I install the LAMP portion after calling it with root permissions, I have no UI.  Personally, I need a UI.  Am I not understanding this?  I figured once I install the LAMP packages and restart the server, there would be a user interface but nothing...  Any idea's?  Any help would be great!

Links I've gone to:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
[https://help.ubuntu.com/community/Tasksel#Command%20line%20arguments](https://help.ubuntu.com/community/Tasksel#Command%20line%20arguments)
And a few online

/Deric

---

### Post by pirateghost on 2010-02-05
installing LAMP does not give you a UI.  you will need to install a desktop.
sudo apt-get install ubuntu-desktop

---

### Post by D-rock on 2010-02-05
> **pirateghost said:**
> installing LAMP does not give you a UI.  you will need to install a desktop.
sudo apt-get install ubuntu-desktop

I.
Love.
You :D

Thanks for the very quick help!

---

