---
title: "libapache2-mod-php5 (--configure):  subprocess install"
date: 2015-10-07
forum: Installation &amp; Upgrades
---

### Post by Tushar_Niras on 2015-10-07
Hi Team,

I've installed Ubuntu 14.04 LTS Server and Apache2 on it
But I'm getting getting following error while installing :**libapache2-mod-php5**
[B]
dpkg: error processing package libapache2-mod-php5 (--configure):  subprocess installed post-installation script returned error exit status 1 Setting up php5 (5.5.9+dfsg-1ubuntu4.13) ... Errors were encountered while processing:  libapache2-mod-php5 E: Sub-process /usr/bin/dpkg returned an error code (1)


Please Help!!
[/B]

---

### Post by s4shi87 on 2015-10-19
Hey,

I'm stuck on the same issue. I wan't to setup my new vagrantbox and it says:

```
==> default: Setting up libapache2-mod-php5 (5.5.9+dfsg-1ubuntu4.13) ...
: not found: /var/lib/dpkg/info/libapache2-mod-php5.postinst: 2: /etc/apache2/envvars:
==> default: dpkg: error processing package libapache2-mod-php5 (--configure):
==> default:  subprocess installed post-installation script returned error exit status 127
==> default: Errors were encountered while processing:
==> default:  libapache2-mod-php5
==> default: E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Thanks for help. Best

---

