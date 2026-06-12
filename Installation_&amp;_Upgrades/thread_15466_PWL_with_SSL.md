---
title: "PWL with SSL"
date: 2005-02-14
forum: Installation &amp; Upgrades
---

### Post by Jezze on 2005-02-14
I'm trying to install a Perl module called Crypt::SSLeay

the problem is when running the command:

perl -MCSPAN -e 'install Crypt::SSLeay'

This creates a Makefile for this module that tries to use the cc command to link but Ubuntu as far as I understand doesn't use this. Am I missing some package or is CSPAN creating a faulty Makefile?

Also It complains about not knowing where the openssl build directory is, I have installed the openssl package but it did not come with a build directory, what should I do?

---

### Post by cblack on 2005-02-14
libcrypt-ssleay-perl exists in universe.

But it sounds like you're unable to build it because you don't have a compiler installed or the libssl-dev package.

---

### Post by Jezze on 2005-02-14
I managed to fix it.... thanx anyway!

---

