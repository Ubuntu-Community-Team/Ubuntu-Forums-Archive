---
title: "Filezilla Upgrade &gt; 3.0.0.4"
date: 2008-01-09
forum: Installation &amp; Upgrades
---

### Post by phreaky- on 2008-01-09
OS: Ubuntu 6.10

1st of all I am still learning and I want to get it right. I am reading a book 'Beginning with Ubuntu Linux 2nd Edition' But it doesn't cover stuff like this.

I tried to install FileZilla 3.0.0.4 version. Because I need a special feature (FTPS Explicit) from it. The version which you can install trough Synaptic (3.0.0.0_ is missing that feature. 

So I did read the INSTALL/README of FileZilla and installed 

- wxWidgets 2.8.6
- libidn
- GnuTLS 2.0.4

After a lot of compiling and adding missing stuff to get GNUTLS to work I finally got it right but now I get the following message. 

[i]*** 'libgnutls-config --version' returned 2.0.4, but LIBGNUTLS (1.4.0)
*** was found! If libgnutls-config was correct, then it is best
*** to remove the old version of LIBGNUTLS. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If libgnutls-config was wrong, set the environment variable LIBGNUTLS_CONFIG
*** to point to the correct copy of libgnutls-config, and remove the file config.cache
*** before re-running configure[/i]

**What should I do? I really don't have a clue what I should put exactly in /etc/ld.so.conf or how to delete the old libgnutls (1.4.0) or where to modify LD_LIBRARY_PATH.**

I did a whereis on libgnutls and it sais:
libgnutls: /usr/local/lib/libgnutls.so /usr/local/lib/libgnutls.la /usr/local/lib/libgnutls.a

---

