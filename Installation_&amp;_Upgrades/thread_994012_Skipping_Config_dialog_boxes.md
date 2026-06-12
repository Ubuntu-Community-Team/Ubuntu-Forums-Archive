---
title: "Skipping Config dialog boxes"
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by Causer1984 on 2008-11-26
This is a problem that seems so basic, I'm surprised that I cannot find out how to do it with google. Sorry if I bashed in the wrong thing into search and this has been asked before.

I want to install libpam-ldap without it pulling ldap-auth-config, or more specifically without it bringing up a debconf dialog box. I have all my config files in place on the computer and since I'm doing this for quite a few computers, I want as silent an install as possible. From the looks of it, preseeding can do this, but I don't know how this will work when invoking apt-get from the commandline. When /etc/ldap.conf exists, it asks me if I want debconf to manage it. If I select yes, it goes through the motions and finishes.

When I uninstall and reinstall libpam-ldap, it remembers that it's already been configured. Is there a flag that I can switch to stop the config dialog box?

Any help gratefully appreciated.

---

### Post by lemming465 on 2008-11-28
The questions are coming from the debconf infrastructure.  You can go with 100% default answers using *export DEBIAN_FRONTEND=noninteractive*.  You can seed answers before install with *dpkg-preconfigure*, I think.  I'm not sure how you customize installation parameter answers in more complex ways without rebuilding the .deb package.  You may have to spelunk in the debian installer documentation to find better answers.

---

### Post by Causer1984 on 2008-12-01
> **lemming465 said:**
> export DEBIAN_FRONTEND=noninteractive

Just the ticket I was after. Many thanks Lemming465

---

