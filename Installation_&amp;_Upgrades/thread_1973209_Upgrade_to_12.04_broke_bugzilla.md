---
title: "Upgrade to 12.04 broke bugzilla"
date: 2012-05-04
forum: Installation &amp; Upgrades
---

### Post by cbryant on 2012-05-04
Had bugzilla 4.2 working just fine previous to upgrading to 12.04 now I get the following error:

/usr/bin/perl: symbol lookup error: lib/x86_64-linux-gnu-thread-multi/auto/Params/Validate/XS/XS.so: undefined symbol: Perl_Gthr_key_ptr

This is when trying to access via apache or when trying to run checksetup.pl

I've searched for this problem which it looks like many had this problem in 2011 but they seem to be related to package dependancies and perl installation errors.  I've not made any modifications to perl except for that done by the upgrade to 12.04.

This is perl 5, version 14, subversion 2 (v5.14.2) built for x86_64-linux-gnu-thread-multi
:(

---

### Post by RJARRRPCGP on 2012-05-04
It means mismatched libraries, one of the libraries must be replaced with a later version! 

It appears that one of the libraries (not mentioned in the error message) is outdated. **XS.so** accessing an outdated library, to be exact.

---

### Post by cbryant on 2012-05-04
Any idea how to tell which one?

---

### Post by spline on 2012-05-05
Hi

I had that exact same problem after upgrading to 12.04.

Let me first that that I am very inexperienced with perl, so I can not say much about any side effects or problems that this solution might produce. I will also not be able to give any further instructions if any other problems arise.

My solution was simply to delete the "i686-linux-gnu-thread-multi-64int" folder inside the "lib" folder of the bugzilla installation. I then ran the "checksetup.pl" script and reinstalled any necessary perl modules.

This fixed it for me, hope this helps.

[edit]
I can see that your folder is called "x86_64-linux-gnu-thread-multi" and not "i686-linux-gnu-thread-multi-64int", so I assume that is the folder you should delete.

---

### Post by vewert on 2012-05-08
I had the same problem after updating to 12.04.  I tried spline's solution and it seems to work for me.

Thanks!

---

### Post by PhoneixS on 2012-05-15
> **spline said:**
> Hi

I had that exact same problem after upgrading to 12.04.
...

My solution was simply to delete the "i686-linux-gnu-thread-multi-64int" folder inside the "lib" folder of the bugzilla installation. I then ran the "checksetup.pl" script and reinstalled any necessary perl modules.

This fixed it for me, hope this helps.
...


Thank you, in my case the module that I have to install after remove the directory was Template.

---

