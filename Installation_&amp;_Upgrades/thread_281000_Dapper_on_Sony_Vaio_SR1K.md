---
title: "Dapper on Sony Vaio SR1K"
date: 2006-10-20
forum: Installation &amp; Upgrades
---

### Post by kliver on 2006-10-20
Trying to install Dapper on a Sony Vaio SR1K with a bootable PCMCIA CD-ROM (Sony Vaio PCGA-CD51).

Choosing install/trying to use the Live CD yields:
can't access tty: job control turned off

And this is it. Didn't find a solution for that on the net.
I however realised that others posted similar problems here before, without success (so I'll try it again).

Now, what I already found out: When trying to install Damn Small Linux, it won't work either, but there is a work around. I just have to adjust the boot options before installation with:

dsl ide2=0×180 nopcmcia (never ask me what it does, but it works).

I tried to use ide2=0×180 nopcmcia as boot options with ubuntu and xubuntu (which obviously would be appropriate for my old laptop) without success - is there no such command or do I somehow need to have something in addition?

Your help would be very much appreciated.

---

