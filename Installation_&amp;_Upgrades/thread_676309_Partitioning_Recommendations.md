---
title: "Partitioning Recommendations"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by jonjonz on 2008-01-23
I am looking for recommendations on swap file size and partitioning for a new Ubuntu 7.10 installation.

This  box is intended to be a basic web server.  We have been running a Ubuntu LAMP 6.06 on an older box for some special web projects, so we are quite happy with Ubuntu. 

The role of this new box is to eventually replace our current web site that now resides on a much older and less robust Windows NT based server.

The basic specifications for the new box:
CPU 3Ghz IBM X5series345
RAM  2.5 Gb
Drives: 
[INDENT]C with 19Gb
 D with 185 Gb[/INDENT]

Proposed partitioning
C  swap file of 4 Gb, 
    15 Gb for data
D  all 185 for executables etc.

We want to install a 7.10 based LAMP environment.  

With 2.5 Gb of memory, would a swap of 2x or 1.5x that size be recommended. 

Our main concern is reliability and stability, and want to minimize having to fiddle with the setup.

Is there any benefit to placing the swap partition and the main executables on different drives?

Most of the reference sources I have read seem to have been written before 2.5 GB of RAM was common.

---

### Post by Lostincyberspace on 2008-01-23
You would probably be fine with half even. I would go about a though.GB.

---

### Post by Pumalite on 2008-01-23
With 2.5 GB of RAM in a Server, 1 GB of /swap is plenty and you can place it in either drive.

---

