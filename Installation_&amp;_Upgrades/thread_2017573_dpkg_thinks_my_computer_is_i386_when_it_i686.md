---
title: "dpkg thinks my computer is i386 when it i686"
date: 2012-07-05
forum: Installation &amp; Upgrades
---

### Post by ibob on 2012-07-05
Hi,

I have a 64bit machine - which I can verify with the command:

 $uname -m
 686

or

 $lscpu
 Architecture:          i686
 CPU op-mode(s):        32-bit, 64-bit

However, if I try to install anything 64 bit dpkg or software centre says:

 package architecture (amd64) does not match system (i386)

This is really strange.  Any ideas what I might have done to get into this situation?  And what can I do to sort this out?

Thanks for your help,

James

---

### Post by ibob on 2012-07-05
Hi,

Just a little update.

If I run: 

$uname -a
Linux jamesdesktop 3.2.0-26-generic-pae #41-Ubuntu SMP Thu Jun 14 16:45:14 UTC 2012 i686 i686 i386 GNU/Linux

Which shows both i686 and i386... hum.

James

---

### Post by oldos2er on 2012-07-05
i686 and i386 are both 32-bit. What processor do you have? If you want to run 64-bit (amd64) programs, you'll need to install 64-bit Ubuntu first.

---

