---
title: "My mistakes in upgrading breezy-&gt;dapper"
date: 2006-08-31
forum: Installation &amp; Upgrades
---

### Post by Minilek on 2006-08-31
In breezy I apt-get upgraded and then dist-upgraded.  After that I changed my /etc/apt/sources.list to use dapper repositories instead of breezy then apt-get upgraded.  I noticed many packages held back and thought something went wrong, so I one-by-one went through each one and apt-get installed it (and apt decided to remove some other packages each time I did this).  I then dist-upgraded (which did nothing).  Now my dapper install is pretty broken.  If I run gdm, for example, things hang right after logging in.  Does anyone know how to fix this?

---

### Post by aysiu on 2006-09-01
I don't know why that happened to you, but you're probably better off backing up and reinstalling than trying to fix this.

---

### Post by randell6564 on 2006-09-01
> **Minilek said:**
> In breezy I apt-get upgraded and then dist-upgraded.  After that I changed my /etc/apt/sources.list to use dapper repositories instead of breezy then apt-get upgraded.  I noticed many packages held back and thought something went wrong, so I one-by-one went through each one and apt-get installed it (and apt decided to remove some other packages each time I did this).  I then dist-upgraded (which did nothing).  Now my dapper install is pretty broken.  If I run gdm, for example, things hang right after logging in.  Does anyone know how to fix this?

Why would you go and manually edit your /etc/apt/sources.list AFTER doing the upgrade?

The list would automatically change WITH the upgrade would it not?

---

### Post by Minilek on 2006-09-01
No.  Running apt-get dist-upgrade doesn't change your sources.list.  You have to do that yourself, but it's easy.  Just replace all instances of breezy with dapper.

---

### Post by aysiu on 2006-09-01
Full instructions are here:
[http://www.psychocats.net/ubuntu/dapper](http://www.psychocats.net/ubuntu/dapper)

---

### Post by randell6564 on 2006-09-01
> **Minilek said:**
> No.  Running apt-get dist-upgrade doesn't change your sources.list.  You have to do that yourself, but it's easy.  Just replace all instances of breezy with dapper.

I'll have to do a dist-upgrade on my test box and see, because I am almost certain that when I did one some time back (before I recieved my Live CD's), it DID save a copy of my Breezy list, but it was now utilizing a Dapper list.

Although, I upgraded by responding to the 'Update Manager' notification.  I DO recall having to first go into Synaptic Package Manager>Settings>Repositories and check some boxes.  I did not actually upgrade from the terminal.

---

