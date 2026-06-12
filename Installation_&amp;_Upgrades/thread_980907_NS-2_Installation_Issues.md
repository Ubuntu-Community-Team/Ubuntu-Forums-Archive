---
title: "NS-2 Installation Issues"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by Chris_networking on 2008-11-13
Hi guys.
My problem has to do with the installation of NS-2.I have downloaded the pieces required but when time comes for ns 2.33 to install after i type the make command it gives me at the end of the output this:

/usr/bin/ld: ns: hidden symbol `__stack_chk_fail_local' in /usr/lib/libc_nonshared.a(stack_chk_fail_local.oS) is referenced by DSO
/usr/bin/ld: final link failed: Nonrepresentable section on output
collect2: ld returned 1 exit status
make: *** [ns] Error 1

After a research i made i discovered that it has to do something with the gcc v4.3.2.I think that there is a mistake in compilation.I get the same output with nam.Required pieces such as tcl,tk are installed smoothly.Has anyone figure it out?
Thanks in advance...

---

