---
title: "Hardy Heron broke Rational App Dev 7.0"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by javaben on 2008-04-26
I have been using IBM Rational Application Developer in Ubuntu 7.10 with out any problems.  Now, after upgrading to H. Heron 8.04 LST, it will no long launch. 

The error log shows a problem locating libxpcom.so

Here's the exact message:

Caused by: java.lang.UnsatisfiedLinkError: /home/myhome/.eclipse/ibm.software.development.platform_7.0.0/configuration/org.eclipse.osgi/bundles/221/1/.cp/libswt-mozilla-gtk-3236.so (libxpcom.so: cannot open shared object file: No such file or directory)

The command 'locate libxpcom.so' gives this response:
/usr/lib/libxpcom.so.0d
/usr/lib/xulrunner/libxpcom.so
/usr/lib/xulrunner-1.9b5/libxpcom.so

So it's obvious I still have at least two libxpcom.so, so the problem appears to be that libxpcom.so was in a directory that was deleted under the new upgrade.

I've found references on the net that this is associated with the move to Firefox 3.0b5 release candidate, so the directory structure must have changed with the Firefox upgrade.

Anyone have any suggestions on how to resolve?

Thanks,

JavaBen

---

