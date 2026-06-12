---
title: "GnuPG installation problem"
date: 2016-05-22
forum: Installation &amp; Upgrades
---

### Post by skippylou on 2016-05-22
Trying to install GnuPG on 16.04LTS.  In the process of installing packages that ./configure asks for I need libgpg-error.  Use "apt-cache search libgpg-error" and I see it shows a libgpg-error0.  "apt-get install libgpg-error0" says it is already installed.  "apt-get install libgpg-error" says package does not exist.

???????????????

---

### Post by Dennis N on 2016-05-22
the gnupg package (gnupg 1.4.20-1ubuntu3) is installed by default in Ubuntu 16.04 and ready to use.

---

### Post by skippylou on 2016-05-22
> **Dennis N said:**
> the gnupg package (gnupg 1.4.20-1ubuntu3) is installed by default in Ubuntu 16.04 and ready to use.


Thanks, what is the command to launch it?

---

### Post by Dennis N on 2016-05-22
The terminal command is **gpg**. The first time it runs, it will create some configuration files and the keyring if I recall. Then you can create or import your keys. In fact, I just now ran it for the first time in 1604 and you should see this:

```
dmn@Roxanne:~$ gpg
gpg: directory `/home/dmn/.gnupg' created
gpg: new configuration file `/home/dmn/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/dmn/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/dmn/.gnupg/secring.gpg' created
gpg: keyring `/home/dmn/.gnupg/pubring.gpg' created
gpg: Go ahead and type your message ...

```

---

