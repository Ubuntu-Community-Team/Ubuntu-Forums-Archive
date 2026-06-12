---
title: "d-i pkgsel/include string openssh-server ??"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by bchill on 2010-06-11
Hello,

Has anyone gotten "d-i pkgsel/include string openssh-server" or similar to work?

Would you share your kickseed file?

Thanks!

Brian

---

### Post by bchill on 2010-06-12
I finally figured out the problem I have been having with 'string' preseeds.

If you use the preseed directive in a kickstart file, you can't have spaces in the string, which means using quotes or no spaces between items and commas. This worked for me:

preseed --owner  d-i pkgsel/include string openssh-server,nfs-kernel-server

Presumably this would work, too:

preseed --owner  d-i pkgsel/include string 'openssh-server nfs-kernel-server'

Some posts alluded to this in a roundabout way, but I don't see this specifically documented anywhere - maybe I just keep missing it.

What's frustrating about this is that there doesn't seem to be any error or warning that the directive has failed. Maybe I missed how to get that behavior, too.

Brian

---

