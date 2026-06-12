---
title: "aufs supported in 13.04 kernel?"
date: 2013-05-14
forum: Installation &amp; Upgrades
---

### Post by brickbat on 2013-05-14
Hi, 

I am currently running 12.10.  I am thinking of upgrading to 13.04 because I am experiencing cpu usage spikes in ssh, which my server uses a lot.  Also, for some reason, I cant use the gui Ubuntu Software Center.  It can't create the window.  All it shows is an outline being redrawn over and over again.  I figure, by upgrading, I should resolve these issues.  My only concern is that I rely on aufs to unify the directory structure of the 12 hdds in my server into one volume.

I heard that there was discussion of aufs not being supported in the kernel after 12.10 and was wondering if someone could tell me if this is true or not.

Thanks,
bb

---

### Post by sum1nil on 2013-06-15
I am running Ubuntu 13.04. The command 'uname -a' results in 
Linux Ubuntand 3.8.0-25-generic #37-Ubuntu SMP Thu Jun 6 20:47:07 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

According to SourceForge: [http://aufs.sourceforge.net/](http://aufs.sourceforge.net/)

The currently available support is (for kernel 3.0 and later - previous kernels seem no longer supported ):
aufs3
aufs3.0, aufs3.1, aufs3.3, aufs3.5 are unsupported since Apr 2013.
Currently aufs3 supports these kernels.
linux-3.x-rcN  	latest
linux-3.9 	last stable
linux-3.8 	still marked as stable [EOL]
linux-3.7 	still marked as stable [EOL]
linux-3.6 	still marked as stable [EOL]
linux-3.4 	last longterm
linux-3.2.x 	still marked as longterm
linux-3.2 	still marked as longterm 

I would say wait a bit longer for the best support unless your a brave soul.
Take care.

---

