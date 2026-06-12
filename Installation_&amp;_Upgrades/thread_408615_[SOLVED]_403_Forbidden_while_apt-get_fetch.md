---
title: "[SOLVED] 403 Forbidden while apt-get fetch"
date: 2007-04-13
forum: Installation &amp; Upgrades
---

### Post by destructchaos on 2007-04-13
when i ran 'sudo apt-get upgrade' this afternoon, i got the following error:

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main linux-image-2.6.20-14-generic 2.6.20-14.23
  403 Forbidden [IP: 91.189.89.6 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-14-generic_2.6.20-14.23_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-14-generic_2.6.20-14.23_i386.deb)  403 Forbidden [IP: 91.189.89.6 80]

if i try to access the address in firefox, the directory listing comes right up.  i've never seen this before.  what am i doing wrong?

thanks.

---

### Post by drbob07 on 2007-04-13
I believe there is a bug in the kernel, so to prevent people from borking their systems, Ubuntu has blocked access for the automatic updater. You can still install the update on your own (by browsing via Firefox), but it might break your system, so I wouldn't reccomend it.

---

### Post by sikity on 2007-04-13
I get the same issue for any of the linux-image-2.6.20-* image.s  I can get to the directory but even downloading the image in firefox fails with the same 403 error.  It seems like the files are not readable.  
I was able to install the debug version of the image.

---

