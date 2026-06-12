---
title: "Dead Nginx after Upgrade 16.04 &gt; 18.04 (i386)"
date: 2019-09-19
forum: Installation &amp; Upgrades
---

### Post by jnap2 on 2019-09-19
Hello

Need some help, last night i upgraed my server from 16.04 to 18.04, almost everything updated successful, the only problem that i had was with Nginx.
No matter what I tried to do, there's no way to bring the server back online.

After some research i saw that the Bionic version of Nginx doesnt support i386, that's what i have installed, old machine started with version 10...

Running simple commands like apt install nginx, give me errors of missing dependices:
- nginx-extras

Tried to apt install nginx-extras, missing:
- perlapi-5.22 (not exists on bionic, there's a perl-base 5.26.1-26) 
- libperl5.22 bionic has the libperl5.26

Downloaded deb package for the nginx-extras and tried to install manually, some missing dependices related to lua, so just did the same, deb files, dpkg to install, and finally forced the nginx-extras.
Installed, but in the end, it didn't run, on start it tries to load a so file... 
"error while loading shared libraries: libperl.so.5.22: cannot open shared object file: No such file or directory"

I thought in put in libraries folder the missing files, but when getting the deb package and running dpkg, it complains about some other perl packages, so i gave up.

So i'm kind of stuck and i can't make my server to start.

Any ideia how to solve my problem?

Thanks

---

