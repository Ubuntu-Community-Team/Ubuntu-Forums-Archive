---
title: "Dell Optiplex 320 Install Issues - Kernel Bug"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by dublindog on 2007-01-24
Dell has posted in their forums that a fix was found for the install issues, being somewhat new to Ubuntu is there a daily build or some other process where I might be able to download a build with this kernel bug fix in it?

Thanks in advance!
Mike

--------------------------------------------------------------------------------------

[http://lists.us.dell.com/pipermail/linux-desktops/2007-January/000148.html]("http://lists.us.dell.com/pipermail/linux-desktops/2007-January/000148.html")

Optiplex 320 SATA problem - solution found
John_Hull at Dell.com John_Hull at Dell.com
Tue Jan 23 12:35:53 CST 2007

    * Previous message: D520 in knoppix based distro doesn't connect
    * Next message: Thank you Dell for the ieee1394 drivers for RHEL4..
    * Messages sorted by: [ date ] [ thread ] [ subject ] [ author ]

ATI/AMD has found the solution to the SATA controller install problems
many people have been experiencing with Linux on the Optiplex 320. The
problem is due to a kernel bug where the ahci driver was hogging all of
the SATA ports incorrectly: [http://lkml.org/lkml/2006/11/22/264](http://lkml.org/lkml/2006/11/22/264). This
fix is now upstream in 2.6.20, and should be in the next round of
updates for the enterprise Linux distros, as well as any upcoming
distributions that use kernel 2.6.20 or later. 

	John

John A. Hull
Manager, Linux OS Development
Dell Inc.

---

### Post by dcstar on 2007-01-25
> **dublindog said:**
> Dell has posted in their forums that a fix was found for the install issues, being somewhat new to Ubuntu is there a daily build or some other process where I might be able to download a build with this kernel bug fix in it?
........

I'm not sure the current install media will ever have things like this patched into them, you may have to wait for a new version that uses that kernel to appear (which could take a while).

If you had an existing working system then you could compile your own kernel.

---

### Post by dublindog on 2007-01-25
David-

Thank you for the reply.  The challenge is that because of the nature of the bug prevents the system from being loaded, I don't have a working system to recomplie the kernel with.  

Hmmm... could I recompile the kernel for a live CD to be able to get an install to work?

Thanks,
Mike

---

