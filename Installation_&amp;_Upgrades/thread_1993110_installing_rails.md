---
title: "installing rails"
date: 2012-06-01
forum: Installation &amp; Upgrades
---

### Post by jejoony on 2012-06-01
Masters,
im trying to install rails to my machine but i am getting the following error when i run:

$ sudo apt-get install ruby-rvm
...
...
...
dpkg-statoverride: error: syntax error: unknown group 'admin' in statoverride file
dpkg: error processing ruby-rvm (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libstdc++6-4.6-dev (4.6.3-1ubuntu5) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 ruby-rvm
E: Sub-process /usr/bin/dpkg returned an error code (1)

any suggestions? thank you

---

### Post by Cheesemill on 2012-06-01
Yep, the package is broken. Install using these instructions instead:

[https://rvm.io/rvm/install/](https://rvm.io/rvm/install/)

---

