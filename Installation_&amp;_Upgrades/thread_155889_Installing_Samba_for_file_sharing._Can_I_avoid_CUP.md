---
title: "Installing Samba for file sharing. Can I avoid CUPS? Should I?"
date: 2006-04-05
forum: Installation &amp; Upgrades
---

### Post by motionsiren on 2006-04-05
Im building a dedicated file server that will never see a printer in it's life time. I noticed that when getting ready to install samba:

```

admin@tic:/home$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libcupsys2-gnutls10 libkrb53 samba-common
Suggested packages:
  krb5-doc krb5-user samba-doc
The following NEW packages will be installed:
  libcupsys2-gnutls10 libkrb53 samba samba-common
0 upgraded, 4 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/4706kB of archives.
After unpacking 11.6MB of additional disk space will be used.
Do you want to continue [Y/n]?

```

It's getting ready to add CUPS related software to my system. Is there a way / or a different package in the respository to install samba WITHOUT cups support? 

Either way, I guess I don't really care if nothing happens with CUPS that i don't know about (config, running, etc.).... I don't see how it could damage anything as I wont be using it.

Basically, I don't feel in control and would like to know what my options are to continue building my system.

This is a server install, no X, only console. (mmm).

---

### Post by skirkpatrick on 2006-04-06
It looks to me like it's only a library for CUPS, not CUPS itself.  If you don't want Samba to have CUPS support, you'll probably have to build it from source.

---

### Post by motionsiren on 2006-04-06
makes sense. thanks. 

just needed to hear it, perhaps. ;)

---

