---
title: "phpize not found"
date: 2007-02-05
forum: Installation &amp; Upgrades
---

### Post by graylion on 2007-02-05
I installed php5-dev and when trying to install ocl8 I get this:

root@diskslave:/usr/local/src# pecl install oci8
/tmp/glibctestFrAQ5J:1:22: error: features.h: No such file or directory
downloading oci8-1.2.3.tgz ...
Starting to download oci8-1.2.3.tgz (83,591 bytes)
....................done: 83,591 bytes
10 source files, building
running: phpize
sh: phpize: command not found
ERROR: `phpize' failed

any suggestions?

thanks

---

### Post by lhtown on 2007-02-05
I am not familiar with that package. I would guess that this is a dependency problem. Probably either you are trying to compile it with the wrong version of a package or else a needed dependency is missing entirely.

---

### Post by Boris Hajduk on 2007-02-12
First, double-check that you installed the php[4|5]-dev package.
apt-get install php4-dev 

Then verify if 'phpize' is in your PATH

---

