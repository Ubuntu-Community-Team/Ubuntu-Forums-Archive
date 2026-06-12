---
title: "Installing APC for PHP"
date: 2006-07-26
forum: Installation &amp; Upgrades
---

### Post by ph00dz on 2006-07-26
Weirdness trying to install APC for PHP5...

This is what happens... any ideas?

tdesigns@tdesigns-cluster2:~$ sudo pecl install apc
downloading APC-3.0.10.tgz ...
Starting to download APC-3.0.10.tgz (85,818 bytes)
....................done: 85,818 bytes
35 source files, building
running: phpize
Configuring for:
PHP Api Version:         20041225
Zend Module Api No:      20050922
Zend Extension Api No:   220051025
cp: cannot stat `shtool': No such file or directory
cp: cannot stat `libtool.m4': No such file or directory
cp: cannot stat `config.sub': No such file or directory
cp: cannot stat `config.guess': No such file or directory
cp: cannot stat `ltmain.sh': No such file or directory
cat: ./build/libtool.m4: No such file or directory
chmod: cannot access `/tmp/tmpYGCXzG/APC-3.0.10/build/shtool': No such file or directory
shtool at '/tmp/tmpYGCXzG/APC-3.0.10/build/shtool' does not exist or is not executable.
Make sure that the file exists and is executable and then rerun this script.

ERROR: `phpize' failed

---

### Post by ajslater on 2007-05-26
% sudo apt-get install php5-dev apache2-dev

---

