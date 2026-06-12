---
title: "PHP7 now not working on Xubuntu 16.04"
date: 2016-05-30
forum: Installation &amp; Upgrades
---

### Post by jimford on 2016-05-30
After a recent update I found php was not rendering a php web page and would show only the script text.

I tried googling for the problem, but none of the suggested fixes worked.

I ended up purging php, including manually removing the /etc/php directory.

I then reinstalled php, and got php7 installed without errors.

A web page script still wouldn't render, because libapache2-mod-php was not installed.

I tried installing libapache2-mod-php (several times!) but always got the following error:

> Setting up libapache2-mod-php7.0 (7.0.4-7ubuntu2.1) ...
dpkg: error processing package libapache2-mod-php7.0 (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            dpkg: dependency problems prevent configuration of libapache2-mod-php:
 libapache2-mod-php depends on libapache2-mod-php7.0; however:
  Package libapache2-mod-php7.0 is not configured yet.

dpkg: error processing package libapache2-mod-php (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libapache2-mod-php7.0
 libapache2-mod-php
E: Sub-process /usr/bin/dpkg returned an error code (1)

I'm really stumped here and would be grateful for some advice, please!

Jim

---

