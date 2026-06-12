---
title: "Help! Update to 7.10 gone wrong with ubuntu-keyring"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by armeria on 2007-10-20
I got something wrong when I upgrated my system to 7.10 following the system->administration->update->upgrate to 7.10.

During the upgrating, there was an error message said ubuntu-keyring got some error and the upgrate stopped. When I wanted to fix the problem, the system showed the following error message:

Setting up ubuntu-keyring (2007.06.11) ...
gpg: symbol lookup error: /usr/local/lib/libreadline.so.5: undefined symbol: PC
gpg: symbol lookup error: /usr/local/lib/libreadline.so.5: undefined symbol: PC
dpkg: error processing ubuntu-keyring (--configure):
subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of ubuntu-minimal:
ubuntu-minimal depends on ubuntu-keyring; however:
Package ubuntu-keyring is not configured yet.
dpkg: error processing ubuntu-minimal (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
ubuntu-keyring
ubuntu-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)

Does anyone know how to fix this error? Thanks a lot for you help!

---

### Post by s_raghu20 on 2008-03-10
Hi,

I have a fresh installation of Gutsy on an HP Compaq 6710b.  I was trying to get some packages from medibuntu when I noticed this error message for me too.

```

gpg: symbol lookup error: /usr/local/lib/libreadline.so.5: undefined symbol: PC

```

Any luck for you ?

---

