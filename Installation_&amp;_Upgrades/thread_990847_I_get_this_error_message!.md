---
title: "I get this error message!"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by Morphed1 on 2008-11-23
E: samba-common: subprocess post-installation script returned error exit status 10
E: samba: dependency problems - leaving unconfigured
E: smbclient: dependency problems - leaving unconfigured
E: smbfs: dependency problems - leaving unconfigured
E: pyneighborhood: dependency problems - leaving unconfigured
E: qtsmbstatus-server: dependency problems - leaving unconfigured
E: system-config-samba: dependency problems - leaving unconfigured
E: samba-dbg: dependency problems - leaving unconfigured

This happens when I'm downloading on package manager in my linux mint 5 64bit. I'm hoping I can get some answers here on what is wrong.

Thanks in advance

---

### Post by cdtech on 2008-11-23
Have you tried:
```
sudo dpkg --configure -a && sudo apt-get -f install
```

---

### Post by Morphed1 on 2008-11-23
This is what i get:

kjetil@kLin ~ $ sudo dpkg --configure -a && sudo apt-get -f install
Setting up samba-common (3.0.28a-1ubuntu4.7) ...
dpkg: error processing samba-common (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 3.0.28a-1ubuntu4.7); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pyneighborhood:
 pyneighborhood depends on smbclient (>= 3.0.22); however:
  Package smbclient is not configured yet.
dpkg: error processing pyneighborhood (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of samba:
 samba depends on samba-common (= 3.0.28a-1ubuntu4.7); however:
  Package samba-common is not configured yet.
dpkg: error processing samba (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-samba:
 system-config-samba depends on samba; however:
  Package samba is not configured yet.
dpkg: error processing system-config-samba (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of qtsmbstatus-server:
 qtsmbstatus-server depends on samba; however:
  Package samba is not configured yet.
dpkg: error processing qtsmbstatus-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of samba-dbg:
 samba-dbg depends on samba (= 3.0.28a-1ubuntu4.7); however:
  Package samba is not configured yet.
dpkg: error processing samba-dbg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of smbfs:
 smbfs depends on samba-common (= 3.0.28a-1ubuntu4.7); however:
  Package samba-common is not configured yet.
dpkg: error processing smbfs (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 samba-common
 smbclient
 pyneighborhood
 samba
 system-config-samba
 qtsmbstatus-server
 samba-dbg
 smbfs


any clues?

---

