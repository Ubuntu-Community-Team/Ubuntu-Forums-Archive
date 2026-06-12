---
title: "slapd 2.4.15-1ubuntu3.1 apt-get problem"
date: 2010-09-06
forum: Installation &amp; Upgrades
---

### Post by mikebern on 2010-09-06
I have a server running 9.04.

I just did an apt-get dist-upgrade and it had a problem installing slapd to fix a security problem.

Here is the output from apt-get:
Setting up slapd (2.4.15-1ubuntu3.1) ...
  Backing up /etc/ldap/slapd.conf in /var/backups/slapd-2.4.151ubuntu3... done.
chown: invalid argument: `'
dpkg: error processing slapd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 slapd
E: Sub-process /usr/bin/dpkg returned an error code (1)

Looking for hints on how to get the new slapd install because it
fixes a security problem.

I am hoping that someone else has seen this problem and give a quick fixes.

The server is running 9.04

A bug report # 632051

---

