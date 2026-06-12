---
title: "Why doesn't the install set /etc/hostname?"
date: 2014-03-29
forum: Installation &amp; Upgrades
---

### Post by DetroitDoc on 2014-03-29
I'm working with a startup setting up a bunch of servers.  So I'm documenting the steps.  Is it just me or is it an oversight that the installation doesn't set /etc/hostname?

Doc

---

### Post by Iowan on 2014-03-29
It's been awhile since I set up a server (or desktop, for that matter), but I thought there was a selection for host name.

---

### Post by steeldriver on 2014-03-29
certainly seems like an oversight... @DetroitDoc perhaps you should mention which installer and which Ubuntu version?

---

### Post by DetroitDoc on 2014-03-29
It does ask for the hostname during the install.  It does put entries in /etc/hosts.   But it doesn't create /etc/hostname.

Sorry I should have mentioned the version.  This is Ubuntu Server 13.10.

Thanks!
Doc

---

### Post by SeijiSensei on 2014-03-29
I haven't installed Debian in a long while, but [this thread from 2012](https://lists.debian.org/debian-user/2012/02/msg00970.html) indicates that it creates /etc/hostname, so if Ubuntu does not that had to be a decision by the Ubuntu developers.  However there are some subtle issues raised in that thread that I have wondered about as well.

I came from RedHat to Ubuntu and was accustomed to entering a fully-qualified domain name when prompted for the hostname, but Ubuntu and Debian specifically ask for just the host part.  That thread points to some issues using just the host part creates when installing other common software like Postfix.  Perhaps not creating /etc/hostname is just an oversight on the part of the developers, but maybe there are some non-obvious reasons that only the developers really understand.

---

