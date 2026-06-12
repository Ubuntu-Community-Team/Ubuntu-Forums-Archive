---
title: "Upgrade or new install with saved /home?"
date: 2013-06-04
forum: Installation &amp; Upgrades
---

### Post by Azyx on 2013-06-04
Hi.
I have a Ubuntu 10.04LTS with one root-partition (19,3GiB 51% occupied), one /home (106,7GiB (93%) occupied) and a swap 2.0GiB on a 128GiB disk.

What is recommended? Install i new Ubuntu 12.04LTS and save /home or make an upgrade from the update manager?

I have now 4GB RAM and what is the cons and pros for 32 vs 64bit system?

I have tested my machine with a live-USB 12.04.2 and it worked fine. I had problem with the graphic with 12.04.0.


Thanx for all tips.

PS. for years ago I have a lot of trubble with upgrade, but there have probably happened a lot in this area....

/Cheers

---

### Post by Cheesemill on 2013-06-04
Are you running 32-bit at the moment?

If so then I would recommend a fresh installation of 12.04, but the 64-bit version.

If you want to stay with 32-bit then you could try the upgrade process, but again I would probably go for a fresh installation as so much has changed between 10.04 and 12.04.

An advantage of doing a fresh installaion is that you can be up and running in 10 minutes, whereas the upgrade process takes hours and may or may not work.

---

### Post by ajgreeny on 2013-06-04
I suggest a clean install.  The changes between 10.04 and 12.04 were enormous, and though many upgraders managed it OK, a lot had a variety of problems.

Mind you, I have never upgraded and always clean installed every time since 5.10, when I first started using ubuntu.

Perhaps try upgrading and see how things work.  As you have a separate /home partition there is nothing to be lost, and if it doesn't work, you can just clean install over the messed up system.

---

### Post by Azyx on 2013-06-04
Ok. Thanx Cheesemill. I have now a 32-bit system. Seems to bee best way with a new install....

Aren't  many application/drivers 64-bit less developed (more bugs) than  32-bits? Are there other benefits with 64-bit than you can use more  than approx 3GB memory? (But with PAE on 32-bit you can use more)

I have a Core Duo (NOT Core 2 Duo) processor.

---

### Post by Cheesemill on 2013-06-04
> **Azyx said:**
> Aren't  many application/drivers 64-bit less developed (more bugs) than  32-bits? Are there other benefits with 64-bit than you can use more  than approx 3GB memory? (But with PAE on 32-bit you can use more)

This may have been true 5 years ago when 64-bit was in its infancy but nowadays 64-bit applications are just as polished as the 32-bit versions. They both use exactly the same source code anyway, just compiled for a different architecture.

Although you can use PAE to address more than 3GB of RAM it's an ugly hack and you're better off using a 64-bit OS instead, you may want to read about what Linus thinks of PAE...
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)

At the end of the day if your hardware supports 64-bit you should use it, there's no point crippling your hardware by running a 32-bit OS.

---

### Post by Azyx on 2013-06-04
> **Cheesemill said:**
> This may have been true 5 years ago when 64-bit was in its infancy but nowadays 64-bit applications are just as polished as the 32-bit versions. They both use exactly the same source code anyway, just compiled for a different architecture.

Although you can use PAE to address more than 3GB of RAM it's an ugly hack and you're better off using a 64-bit OS instead, you may want to read about what Linus thinks of PAE...
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)

At the end of the day if your hardware supports 64-bit you should use it, there's no point crippling your hardware by running a 32-bit OS.

Okey. Seems right!

---

