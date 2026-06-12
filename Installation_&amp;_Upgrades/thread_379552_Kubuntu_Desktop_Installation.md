---
title: "Kubuntu Desktop Installation"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by bparham on 2007-03-08
I'm trying to install Kubuntu on my system in addition to Ubuntu. I'm doing this by typing:

```
sudo aptitude install kubuntu-desktop
```

I didn't receive any errors the first time I attempted this install, however the actual Kubuntu desktop is no where to be found. Thinking that I had an installation problem I reran the installation; I'm now receiving the following message.

```
Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
newaliases: fatal: myorigin parameter setting must not contain multiple values: brad-desktop: bradparham@fuse.net
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up postfix (2.2.10-1ubuntu0.1) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
newaliases: fatal: myorigin parameter setting must not contain multiple values: brad-desktop: bradparham@fuse.net
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 postfix
brad@brad-desktop:~$ /usr/share/postfix/main.cf.dist

```

I've gone in and am trying to alter /etc/postfix/main.cf, but I can't find the error that is being referred to above. Suggestions??

---

### Post by zvacet on 2007-03-09
[http://www.psychocats.net/ubuntu/kde]("http://www.psychocats.net/ubuntu/kde")

---

