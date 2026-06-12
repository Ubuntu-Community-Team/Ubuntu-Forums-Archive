---
title: "[SOLVED] Compiler OpenSSH Problem"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by winkerbean on 2007-10-23
I'm trying to install OpenSSH via compilation, since the apt-get method does not seem to work.  (See here:[http://ubuntuforums.org/showthread.php?p=3558237&posted=1]("http://ubuntuforums.org/showthread.php?p=3558237&posted=1") for details.)

Now, when compiling, I get the following:
[INDENT]configure: error: *** Can't find recent OpenSSL libcrypto (see config.log for details) ***[/INDENT]

Any suggestions?

---

### Post by winkerbean on 2007-10-25
I got it!  I had to download the OpenSSL implementation from [http://www.openssl.org/source/]("http://www.openssl.org/source/") and compile from source.  For whatever reason, the apt-get suggestion on other pages in the forum did not work.  C'est la vi.

---

