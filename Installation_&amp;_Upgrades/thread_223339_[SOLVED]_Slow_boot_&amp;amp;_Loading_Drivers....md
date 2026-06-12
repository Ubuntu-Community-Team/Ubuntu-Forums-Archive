---
title: "[SOLVED] Slow boot &amp;amp; Loading Drivers..."
date: 2006-07-26
forum: Installation &amp; Upgrades
---

### Post by KevinRJohnson on 2006-07-26
Hey all,

I just upgraded my old Dell Inspiron 8200 from Breezy to Dapper.  Went really well and I have to say all in all I'm most impressed.  

There is one small snag.  When I try to boot my system it spends about 2 min on "Loading Drivers..." before it fails and moves on with the boot sequence.  Once I'm logged in everything is fine, but the 2+ min wait for login is something that will rankle me until I fix it.  How do I get it to tell me what failed (or better yet what and WHY)?  Any ideas?

Thanks,
Kevin R. Johnson

---

### Post by bluevoodoo1 on 2006-07-26
When it gets to Loading Drivers.... try pressing Ctrl+c to get past it. Mine hangs on that from time to time and I haven't gotten to the bottom of it yet...

---

### Post by KevinRJohnson on 2006-07-27
Is there any way I can see what drivers its trying to load though?  If I knew I might be able to fix it instead of relying on a ad-hoc solution like that.  I like Ubuntu, everything else works and I'd like to see Dapper hold the perfect record.

---

### Post by tinsami1 on 2006-07-28
I have a similar condition here.  Have posted a similar thread a few days ago without any response.  I've tried other kernels (686-smp and server) to no avail.  I've compiled my own and it was suddenly performing as expected.  But the kernel I have is not up-to-date (2.6.15-7), so I'm searching for the latest Ubuntu kernel source package to install.

---

### Post by KevinRJohnson on 2007-07-19
Sorry I've been so slow with this.  Turns out I had to blacklist a bad wifi driver on my old Ubuntu install to fix the original problem and then it worked like a champ.  Of course the newest version of Ubuntu had no such problem :-)

---

