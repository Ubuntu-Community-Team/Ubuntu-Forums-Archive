---
title: "Ubuntu 10.10 + install new software"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by oliv66 on 2010-10-13
Hi all,

I installed Ubuntu 10.10 from scratch with no problem. I updated and upgraded and installed several software.

when installaing Adobe reader or any other extra software, I have always the same issue described below

```
sudo apt-get install acroread 
[sudo] password for olivier: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  libldap2 libgnome-speech7
The following NEW packages will be installed:
  acroread
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 63.4MB of archives.
After this operation, 152MB of additional disk space will be used.
Get:1 http://archive.canonical.com/ubuntu/ maverick/partner acroread i386 9.4-1maverick1 [63.4MB]
Fetched 63.4MB in 8min 17s (128kB/s)                                           
Preconfiguring packages ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: invalid distance too far back'
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/acroread_9.4-1maverick1_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/acroread_9.4-1maverick1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So, I tried to use sudo apt-get autoclean, sudo apt-get autoremove, sudo dpkg --configure -a with no success again

I removed manually all the files in /var/cache/archives/

It does not work.

what could I do?

Thanks for your help,

Olivier

---

### Post by oliv66 on 2010-10-13
Hi all,

I found the problem.

Eset Nod32 for linux desktop created the problem.

I removed eset and now it works....

Olivier

---

### Post by efpob on 2010-10-15
Cheers for that - I had the exact same trouble.  Can't believe I didn't figure it out myself!!

---

### Post by oliv66 on 2010-10-16
it is a pity because eset is a good AV but still in beta. The final version should be released in December.

I am using Bitdefender for Unices, free of charge. the key is valid for 1 year but can be renewed.

in the past, eset had some issues with 0OO 3.2. hope they will fix all issues.

Have a nice weeekend,

Olivier

---

