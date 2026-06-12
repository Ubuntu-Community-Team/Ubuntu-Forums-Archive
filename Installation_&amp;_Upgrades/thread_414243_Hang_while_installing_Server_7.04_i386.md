---
title: "Hang while installing Server 7.04 i386"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by ^KrS^ on 2007-04-19
I'm trying to install my toasty new server, the install gets to apt-install reiserfsprogs (seen in ALT-4) and hangs.

I'm installing without formatting (have data i HAVE to keep on that drive) two partitions, a main reiserfs part and a 1G swap part.

If i CTRL-C it tries to continue with setting up the partitioner, but again hangs, CTRL-C doesn't help progress after that.

Any ideas out there?

---

### Post by ^KrS^ on 2007-04-19
I resorted to clearing off my 250G in my HD24 and copied the data onto that, did a full format install and it worked fine, must be an issue in the script for not formatting.

you'd think they would catch somethin like that in beta hahah

---

