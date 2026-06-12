---
title: "make: command not found Can someone please explain"
date: 2006-12-03
forum: Installation &amp; Upgrades
---

### Post by Bill007 on 2006-12-03
Kia Ora All

Can some one look at the botom Line and tell me how to fix this

Executing /usr/bin/perl Makefile.PL  && make ..
                                                                                                    > 
Checking for OpenSSL-0.9.6j or 0.9.7b or newer...
That's is newer than what this module was tested with (0.9.6j
or 0.9.7b). You should
consider checking if there is a newer release of this module
available. Everything will probably work OK, though.
You have OpenSSL-0.9.8b installed in /usr
*** Could not figure out which C compiler was used to compile /usr/bin/openssl. It is essentiall tha
t OpenSSL, perl, and Net::SSLeay are compiled with the same compiler and flags. Mixing and matching 
compilers is not supported. at Makefile.PL line 140.
Checking if your kit is complete...
Looks good
Checking if your kit is complete...
Looks good
Writing Makefile for Net::SSLeay::Handle
Writing Makefile for Net::SSLeay
sh: make: command not found

Thanks if you can help Bill007

---

### Post by Sef on 2006-12-03
Have you installed build-essential?   If not, then Applications > Accessories > Terminal, then

```
sudo aptitutde update then sudo aptitude install build-essential
```

Also you may want to read [How to install Anything]("http://monkeyblog.org/ubuntu/installing/") in Ubuntu.

---

