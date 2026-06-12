---
title: "how can I install G++ 4.2.3. for Matlab Mex on Ubuntu 11.10?"
date: 2011-10-30
forum: Installation &amp; Upgrades
---

### Post by Deneck on 2011-10-30
Hi,

I am trying to compile an application for Matlab (mpgwrite).

First I got the make error 127, so I changed the Makefile by including the path to matlabs mex.

However, now I have the problem that mex needs GCC 4.2.3, but the package manager does not include any version lower than 4.4.

I then downloaded the deb package (g++_4.2.3-1ubuntu3_amd64.deb) manually and tried to have it installed by the Ubuntu Software Center. This did not work.

I am pretty sure you already figured, I am new to this ;)

So, how can I tell ubuntu to install this older version?

thanks a lot,
Deneck

---

### Post by gigix85 on 2011-11-17
Unfortunately you will most likely need to compile your gcc version from source and tell Matlab  where to look for it in your mexopts.sh (created from Matlab command "mex -setup"). I did that on Ubuntu 11.04 for gcc 4.3 with Matlab R2011a and it worked like a charm. Not sure it is going to be as smooth on 11.10 though.

---

