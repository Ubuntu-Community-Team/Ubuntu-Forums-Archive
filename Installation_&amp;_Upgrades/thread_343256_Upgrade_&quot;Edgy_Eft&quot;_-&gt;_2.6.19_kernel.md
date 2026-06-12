---
title: "Upgrade &quot;Edgy Eft&quot; -&gt; 2.6.19 kernel"
date: 2007-01-21
forum: Installation &amp; Upgrades
---

### Post by eztoril on 2007-01-21
Hi all,

I recently successfully upgraded my kernel from the Edgy 2.6.17.10 kernel to 2.6.19 kernel (thanks, Theimon).

However, I wonder if I have to change the repository entries in my 'sources.list' file from 'edgy' to e.g 'fiesty'?

I assume that the upgrades I otherwise is downloading is compatible to kernel 2.6.17.10 and not 2.6.19. Is my assumption correct?

Thanks in advance!

Best regards,
Martin

---

### Post by mkoyle on 2007-01-21
As long as you are dealing with Ubuntu stock kernels, I doubt you will see any problems.  The only problem you might have is that sometime in the future you could get a dependency error.  This seems unlikely to me because usually dependency problems are related to *older* versions of a package.

If you installed the 2.6.19 kernel with 'dpkg -i' or apt-get, you are in good shape.

If you compiled and installed, you might think about going back to the stock kernel, but unless you have problems with your system, don't worry about it.

You're in good shape in my opinion ;)

--Matthew

---

### Post by eztoril on 2007-01-22
Hi again,

Does that mean that I should not change my sources.list (i.e. keep 'edgy' in repository entries)?

Thanks!

Best regards,
Martin

---

