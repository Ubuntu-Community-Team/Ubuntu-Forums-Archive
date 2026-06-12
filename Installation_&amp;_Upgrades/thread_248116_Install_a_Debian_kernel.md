---
title: "Install a Debian kernel?"
date: 2006-08-31
forum: Installation &amp; Upgrades
---

### Post by hizaguchi on 2006-08-31
I'm having some problems with power management in Ubuntu that I don't have in other distros.  More interestingly, they only happen when I'm using one of the SMP kernels.  So I was thinking it would be nice to install a kernel from one of the Debian repositories.  Other than adding the repo to my sources.list and apt-geting the kernel (and possibly adding it to the grub menu), is there anything else I'll need to do to get such a thing working?

---

### Post by GTvulse on 2006-08-31
Absolutely not recommended, not even with a Sid kernel.

You still can do it, by installing kernel-package, grabbing the sources from the Debian repo (in that case you could use an Edgy kernel and get all the goodies) and compile it yourself. I do it all the time. I'm using a 2.16.18-rc5 kernel at the moment because it is the only one that supports my network card OOTB, thanks to a patch I submitted to kernel.org sometime ago...

---

### Post by hizaguchi on 2006-08-31
Heh, I'm stoopid.  I tried it anyway and things broke in a really weird way.  Aptitude fixed it with a little help though.  I love aptitude. :)

I didn't even think of trying an edgy kernel.  I dunno if that would fix my problems though.  I'm worried that something about the way the Ubuntu kernels are built is causing my problems, since it doesn't happen with non-SMP kernels and it doesn't happen with any kernels in other distros.  I was hoping to try some different kernels and find one that works so I'd know what was causing the problem.  I'd prefer not to break my system again though. :)

---

