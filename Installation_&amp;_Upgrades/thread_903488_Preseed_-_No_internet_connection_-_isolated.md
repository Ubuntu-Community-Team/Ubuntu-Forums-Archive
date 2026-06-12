---
title: "Preseed - No internet connection - isolated"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by bkrocker on 2008-08-28
Hi, I'm trying to install ubuntu 8.04 from a network installation using PXE I get through the DHCP configuration and then the installation wants to go out to an external mirror website which is impossible due to the desktop is on an internal switch getting an ip address of 192.168.0.xx from the server which also contains the ubuntu software. I've looked through the preseed file and the only thing I come up with is under the mirror settings of which I set:
d-i mirror/http/hostname string 192.168.0.222 (server host ip)
d-i mirror/http/directory string /tftpboot/pub/ubuntu8_04_1_i386/dists

d-i mirror/http/proxy string

d-i mirror/suite string stable  (don't think this has anything to do with the issue, but included it anyway)

How do I stop the installation from trying to go out looking for an external mirror and not proceeding with the installation.

Any help would be appreciated
Thanks, Blane

---

### Post by bkrocker on 2008-08-28
Hi, I'm trying to install ubuntu 8.04 from a network installation using PXE I get through the DHCP configuration and then the installation wants to go out to an external mirror website which is impossible due to the desktop is on an internal switch getting an ip address of 192.168.0.xx from the server which also contains the ubuntu software. I've looked through the preseed file and the only thing I come up with is under the mirror settings of which I set:
d-i mirror/http/hostname string 192.168.0.222 (server host ip)
d-i mirror/http/directory string /tftpboot/pub/ubuntu8_04_1_i386/dists

d-i mirror/http/proxy string

d-i mirror/suite string stable  (don't think this has anything to do with the issue, but included it anyway)

How do I stop the installation from trying to go out looking for an external mirror and not proceeding with the installation.

Any help would be appreciated
Thanks, Blane

---

### Post by oilchangeguy on 2008-08-28
can a moderator please remove this post? the user already has a thread on this same topic posted.

---

