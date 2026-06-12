---
title: "How to use mirrored repositories from USB install stick?"
date: 2015-10-06
forum: Installation &amp; Upgrades
---

### Post by Marcelo Ruiz on 2015-10-06
Hi,
I have a problem that is driving me crazy.
I have an external HDD connected to my router where I successfully mirrored the ubuntu repositories. The router provides both samba and ftp access to the files (with login credentials).
Files are located at [ftp://myserver/apt-mirrors](ftp://myserver/apt-mirrors)
Now, I don't have a web server installed in the ubuntu USB install stick, and all the tutorials I read require a web server.
How can I access this files?
I tried modifying sources.list to use 

```

deb ftp://user:password@myserver:21/apt-mirrors/mirror/archive.ubuntu.com/ubuntu trusty main restricted universe multiverse

```

but apt-get complains it cannot find the files (and they are there).
This kinds of works because if I remove the login credentials apt-get complains about unsuccessful login.
I guess there should be an easy way to solve this...
Any ideas?

---

