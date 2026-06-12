---
title: "apt-get errors out on attempted update - 6.06.1"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by neill on 2006-10-28
hi

when i try to update a fresh install of 6.06.1 - however i do it (gui or CLI) i get the same error

eg:
sudo apt-get install upgrade ...

Preconfiguring packages ...
(Reading database ... 69825 files and directories currently installed.)
Preparing to replace gzip 1.3.5-12 (using .../gzip_1.3.5-12ubuntu0.1_i386.deb) ...
dpkg (subprocess): unable to execute old pre-removal script: Permission denied
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg (subprocess): unable to execute new pre-removal script: Permission denied
dpkg: error processing /var/cache/apt/archives/gzip_1.3.5-12ubuntu0.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute post-installation script: Permission denieddpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/gzip_1.3.5-12ubuntu0.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

which means precisely zip to me 

i've tried all the various solutions for similar problems and can't fix it

](*,) 

any ideas ??

neill

---

### Post by neill on 2006-10-29
**fixed it** :cool: 

i had setuid flag turned on in the /var partition and this seems to have caused the hissy fit on the part of apt-get

why would i do a thing like that you ask ..... no reason other than it suggests so in the server secirity section of the OFFICIAL ubuntu book :rolleyes: 

if anyone has the connections to the guys & gals who wrote this otherwise excellent tome you might want to point out their tip broke my machine !

thanks

---

