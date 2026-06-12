---
title: "Help with Ubuntu-extra-Keyring"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by eriksson25 on 2010-10-19
Hi, Upgraded my machine from 10.04 to 10.10. But have a big problem, the ubuntu-extras-keyring is unable to install and therefore I am unable to install anything.

I have tried to reinstall it with sudo apt-get --reinstall isntall ubuntu-extras-keyring but it gives the same error

```
eriksson25@eriksson25:~$ sudo apt-get --reinstall install ubuntu-extras-keyring
[sudo] password for eriksson25: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ubuntu-keyring (2010.+09.30) ...
gpg: [don't know]: invalid packet (ctb=2e)
gpg: keydb_get_keyblock failed: eof
gpg: [don't know]: invalid packet (ctb=2e)
gpg: /etc/apt/trusted.gpg: copy to `/etc/apt/trusted.gpg.tmp' failed: invalid packet
gpg: error writing keyring `/etc/apt/trusted.gpg': invalid packet
gpg: [don't know]: invalid packet (ctb=2e)
gpg: keydb_search failed: invalid packet
gpg: key 437D05B5: public key "[User ID not found]" imported
gpg: error reading `[stdin]': invalid packet
gpg: import from `[stdin]' failed: invalid packet
gpg: Total number processed: 0
gpg:               imported: 1
dpkg: error processing ubuntu-keyring (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on ubuntu-keyring; however:
  Package ubuntu-keyring is not configured yet.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
Setting up ubuntu-extras-keyring (2010.09.27) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          Importing extras.ubuntu.com keyring
gpg: [don't know]: invalid packet (ctb=2e)
gpg: keydb_get_keyblock failed: eof
gpg: [don't know]: invalid packet (ctb=2e)
gpg: /etc/apt/trusted.gpg: copy to `/etc/apt/trusted.gpg.tmp' failed: invalid packet
gpg: error writing keyring `/etc/apt/trusted.gpg': invalid packet
gpg: error reading `/usr/share/keyrings/ubuntu-extras-keyring.gpg': invalid packet
gpg: import from `/usr/share/keyrings/ubuntu-extras-keyring.gpg' failed: invalid packet
dpkg: error processing ubuntu-extras-keyring (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on ubuntu-extras-keyring; however:
  Package ubuntu-extras-keyring is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 ubuntu-keyring
 ubuntu-minimal
 ubuntu-extras-keyring
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

plz if anyone have any idees

---

