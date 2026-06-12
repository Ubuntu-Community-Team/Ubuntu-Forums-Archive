---
title: "Where can I download the 9.04 x86 server install iso today?"
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by dcolpitts on 2011-02-05
HELP!!!   I need to find a copy of the 9.04 server x86 install iso asap to facilate an upgrade from 8.10 to 10.10, and it appears that 9.04 has been removed from all the mirrors.

Does anyone know where I can find a copy?

Thanks

dcc

**Update - I've been searching all afternoon and couldn't find it - I posted this and did one more Google search, and immediately found it.  

[http://old-releases.ubuntu.com/releases/jaunty/](http://old-releases.ubuntu.com/releases/jaunty/)

---

### Post by mörgæs on 2011-02-06
I would not recommend such a long upgrade. If you want 10.10, best is to try a live boot and after that a clean install, if it works well.

---

### Post by dcolpitts on 2011-02-06
Already done.  I had to go:
[INDENT]8.10 --> 9.04
9.04 --> 9.10
9.10 --> 10.04.1
10.04.1 --> 10.10
[/INDENT]

Only issues encountered where with grub.lst (my options got reset, which I had expected), and figuring where to add "options loop max_loop=64" to mount more than 8 iso images (previously in modprobe.conf if memory serves me correctly, now a kernel option in grub.lst).

dcc

---

