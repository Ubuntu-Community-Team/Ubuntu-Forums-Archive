---
title: "zinFrameDriver: disagrees about version of symbol module_layout"
date: 2012-03-05
forum: Installation &amp; Upgrades
---

### Post by olexandr.klymenko on 2012-03-05
Hi guys,
I have a task:
Build kernel based on 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 GNU/Linux
(make some minor but necessary changes). At the same time I have proprietary binary drivers (zinFrameDriver, VirtualInputDeviceDriver), so I have to keep compatibility of new kernel with mentioned drivers.
I have built new kernel using manual on ([http://blog.avirtualhome.com/2011/10/28/how-to-compile-a-new-ubuntu-11-10-oneiric-kernel/](http://blog.avirtualhome.com/2011/10/28/how-to-compile-a-new-ubuntu-11-10-oneiric-kernel/))
Finally I got kernel with uname -a:
3.0.0-14-generic #23 SMP Sat Mar 3 02:40:19 EST 2012 i686 GNU/Linux
But when I try to load proprietary drivers I got:
zinFrameDriver: disagrees about version of symbol module_layout
So, how should I build kernel with keeping compatibility?
Thanks in advance.

---

