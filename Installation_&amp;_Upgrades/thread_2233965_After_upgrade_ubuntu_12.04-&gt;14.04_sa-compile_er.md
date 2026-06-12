---
title: "After upgrade ubuntu 12.04-&gt;14.04 sa-compile error"
date: 2014-07-11
forum: Installation &amp; Upgrades
---

### Post by tamer2 on 2014-07-11
Hi,

i am new here and i hope somebody can help me.

i upgrade today my ubuntu Server from 12.04 to 14.04 with apt-get dist-upgrade. After this operation i get now a sa-compile error.

I open my terminal and write sa-compile, i get this error"sa-compile: not compiling; 'spamassassin --lint' check failed!"

When i write apt-get upgrade, i get this error.

tamer@srv:~$ sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up sa-compile (3.4.0-1ubuntu1) ...
Running sa-compile (may take a long time)
Jul 11 23:08:16.494 [1813] info: config: SpamAssassin failed to parse line, "/var/spool/spamassassin/bayes" is not valid for "bayes_path", skipping: bayes_path /var/spool/spamassassin/bayes
sa-compile: not compiling; 'spamassassin --lint' check failed!
dpkg: error processing package sa-compile (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 sa-compile
E: Sub-process /usr/bin/dpkg returned an error code (1)
tamer@srv:~$ 

I think, while upgrading the os something was wrong.

Can anyone help me?

Thanks a lot

Tamer

---

