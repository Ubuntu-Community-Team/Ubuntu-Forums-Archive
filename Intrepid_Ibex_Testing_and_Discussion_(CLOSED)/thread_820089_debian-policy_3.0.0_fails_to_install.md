---
title: "debian-policy 3.0.0 fails to install"
date: 2008-06-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2008-06-05
Hi all, 
 Look at below :-

Setting up debian-policy (3.8.0.0) ...
Can't read doc-base file `/usr/share/doc-base/debian-policy-process'
dpkg: error processing debian-policy (--configure):
 subprocess post-installation script returned error exit status 1as well as 

Errors were encountered while processing:
 debian-policy
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up debian-policy (3.8.0.0) ...
Can't read doc-base file `/usr/share/doc-base/debian-policy-process'
dpkg: error processing debian-policy (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 debian-policy

It would be nice to have any and all workarounds to the issue or if not then I sit tight for the same.

---

### Post by cariboo on 2008-06-06
I have the same problem after an update this morning, I tried using --force-all and still no go.

Jim

---

