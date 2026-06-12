---
title: "Maverick Install error message"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by cazador31 on 2010-10-10
I am trying to upgrade Lucid to Maverick through the upgrade manager. I keep getting this error message and the upgrade stops.  How can I fix this?

W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-proposed/Release](http://us.archive.ubuntu.com/ubuntu/dists/maverick-proposed/Release)

I also get this message:

       GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 15A8576D6E46FCADFailed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-proposed/Release](http://us.archive.ubuntu.com/ubuntu/dists/lucid-proposed/Release)

---

### Post by sikander3786 on 2010-10-10
First of all try to change the Update Servers from System > Administration > Software Sources, select the Main Server preferably and reload the package information. Try again. Is it solved?

---

### Post by cazador31 on 2010-10-10
Didn't work. I still get the same message

---

### Post by sikander3786 on 2010-10-10
This one should work.

[http://www.webupd8.org/2010/05/automatically-import-all-missing.html](http://www.webupd8.org/2010/05/automatically-import-all-missing.html)

[COLOR="Red"]**Edit:**[/COLOR] But before upgrading, it is recommended that you disable all the third party PPAs from Software Sources.

---

### Post by cazador31 on 2010-10-10
Still no luck.  Could it be that the servers are real busy?

---

### Post by sveterv on 2010-10-10
> **cazador31 said:**
> Didn't work. I still get the same message

Try to change to other server than official and your country one. Most of the servers (especially official one) will be overloaded as many people install/upgrade their Ubuntu today as this is official release date for 10.10 version, so many of them will get that kind of message. For me it looks the only problem is with those overloaded servers, but until you post a message that you have resolved problem I hope other people still will give you some advice.

---

### Post by cazador31 on 2010-10-10
I think I'll just wait a day or two before I try again.

Thank you for your help

---

