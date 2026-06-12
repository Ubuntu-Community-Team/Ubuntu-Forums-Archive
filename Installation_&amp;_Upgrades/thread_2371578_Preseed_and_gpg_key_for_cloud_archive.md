---
title: "Preseed and gpg key for cloud archive"
date: 2017-09-16
forum: Installation &amp; Upgrades
---

### Post by densha2 on 2017-09-16
Hi Forum

I have created a preseed configure to automate installing Ubuntu Server.   I would like to add [http://ubuntu-cloud.archive.canonical.com/ubuntu](http://ubuntu-cloud.archive.canonical.com/ubuntu) xenial-updates/pike main as a repository.  However I cannot obtain the gpg key to define it correctly.
d-i apt-setup/local0/repository string [http://ubuntu-cloud.archive.canonical.com/ubuntu](http://ubuntu-cloud.archive.canonical.com/ubuntu) xenial-updates/pike main
d-i apt-setup/local0/source boolean false
d-i apt-setup/local0/key string ???????  

To get around the issue I am using the following.  But would prefer to define the correct key.
d-i debian-installer/allow_unauthenticated boolean true

Does anyone know the syntax to define the key string for the ubuntu?

Thanks

Densha

---

