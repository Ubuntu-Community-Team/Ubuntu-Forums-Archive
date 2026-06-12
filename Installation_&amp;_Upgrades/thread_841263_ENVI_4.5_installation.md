---
title: "ENVI 4.5 installation"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by MarsmanA on 2008-06-26
Hi everybody!
I tried to install the new version of ENVI from a DVD to my ubuntu 7.10 without success. All goes smooth until it starts to install the program. I get this type of message:

The script /usr/local/itt/idl70/bin/post_unpack was not found.
There may be errors setting up the product environment.

The itt folder is a new folder where I want to install ENVI. Can somebody help me please? Thanks.

MarsmanA

---

### Post by birgen haest on 2008-09-24
Same problem here...

will let you know if I come up with a fix...

or maybe you did already?

---

### Post by halhuntley on 2008-11-07
I was able to contact ITT about this and this error occurs when there is no "/bin/csh" available.  One of their solutions was to logically link /bin/csh to /bin/sh.  I'm not sure I want to recommend that.  For my Fedora 9 installation, I just had to do a "yum install csh" and I got the "tcsh" which automatically made a logical link for the csh.  The install then went fine.  

Hal Huntley

---

