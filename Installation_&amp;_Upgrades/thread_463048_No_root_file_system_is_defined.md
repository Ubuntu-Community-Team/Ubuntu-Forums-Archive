---
title: "No root file system is defined"
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by leejames07 on 2007-06-03
Hi i am new to Linux my friend said to get it as it is better than windows at the moment i like what i have seen with Ubuntu. Before i installed i set up a partition ready for Ubuntu but when i try to install manually i choose my partition and get Not root file system is defined edit from partition menu but how would i go about this.

Sorry about this i am new to Linux but so want to use it please help

---

### Post by wpshooter on 2007-06-03
You need to setup the following partitions:

**/** for root
**/home** for home
and a swap partition of about 1 1/2 to 2 times the size of your memory.

---

### Post by leejames07 on 2007-06-03
what would the mount be called for the swap partition /swap?

---

### Post by wpshooter on 2007-06-03
> **leejames07 said:**
> what would the mount be called for the swap partition /swap?

You define the partition **TYPE** as SWAP instead of say EXT3.

---

### Post by leejames07 on 2007-06-03
Thanks just worked that out

---

