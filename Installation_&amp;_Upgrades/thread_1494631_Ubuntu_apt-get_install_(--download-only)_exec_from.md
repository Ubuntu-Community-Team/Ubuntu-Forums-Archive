---
title: "Ubuntu apt-get install (--download-only) exec from another machine on behalf of mine"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by maroloccio on 2010-05-27
I have a server on a network segment with no direct or indirect access  to the Internet.

I want to perform an:

apt-get install <package_name>

  Is there a way to somehow delegate the process of downloading the  required files to another machine by exporting the server configuration  so as to satisfy all dependencies while running:

  apt-get install --download-only <package_name>

  Can, in effect, apt-get install read a configuration from an exported  archive rather than from the local package database?

  Can the list of packages to be downloaded be retrieved, along with an  installation script to perform the installation, instead of the actual  packages? (a further level of indirection which would help me schedule  this with wget at appropriate times...)

---

