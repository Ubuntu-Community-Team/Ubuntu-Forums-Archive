---
title: "Couldn't find package glibc"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by heart_reaver on 2008-05-07
Hi All,

I was installing Oracle 11g on Ubuntu 8.04. But installation prerequisite failed because i didnt installed glibc. 

Checking Recommended glibc version
Expected result: ATLEAST=2.3.4-2.19 
Actual Result: package glibc is not installed
Check complete. The overall result of this check is: Failed <<<<
Problem: Some recommended packages are missing (see above).
Recommendation: You may actually have installed packages which have obsoleted these, in which case you can successfully continue with the install. If you have not, it is recommended that you do not continue. Refer to the product release notes to find out how to get the missing packages and update the system.

Then I try to update repository and try to install. 

:(

But Synaptic was not able to find package glibc.

I have default repository list (default @ installation time)

---

### Post by lemming465 on 2008-05-10
I think the package is called "libc6", and the version in Ubuntu 8.04 is 2.7.  That may be too bleeding edge for Oracle; if you are running Oracle you might want to use an older version of Ubuntu.

---

### Post by heart_reaver on 2008-05-17
Done ... 

I have downloaded package from Ubuntu package list ....

---

### Post by badguyanil on 2010-04-27
i am trying to install Oracle SOA 11g and got the same error. I can download the package but it is in .tar.gz format. How do i install this on ubuntu. I am using 9.10 ver.

i am a newbee here so an elaborate explanation will do good :)

regards

---

