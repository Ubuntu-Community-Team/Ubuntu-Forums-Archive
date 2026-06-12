---
title: "today's update breakdown my dell mini"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by erick_king on 2009-12-05
How can I uninstall this update?
It was just 2 updates: kernels and headers...
The problem is that I recently install drivers for the dell mini as appear on this blog:
[http://otroblogmas.com/configurar-en-ubuntu-9-10-la-tarjeta-grafica-intel-gma500-y-compiz/comment-page-1/#comment-250](http://otroblogmas.com/configurar-en-ubuntu-9-10-la-tarjeta-grafica-intel-gma500-y-compiz/comment-page-1/#comment-250), this is about the intel graphic card since with the normal configuration is ugly...

and it works very well... but then when the updates were installled, an screen informing about the ubuntu with the low graphics mode appears and the everything appears as the beginning: 780*570  

Can I uninstall the updates?

---

### Post by mikewhatever on 2009-12-07
I believe you can fix it following this part of the wiki, not need to remove the newer kernel.

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)
```
Note: after a kernel update, the following steps are needed to re-enable the driver. Prior to a computer reboot, print these instructions so you have them available. Choose a "Recovery" option from the boot menu, and run the following commands from prompt.

# apt-get remove psb-kernel-source
# wget http://gma500re.altervista.org/_altervista_ht/psb-kernel-source_4.41.2-0ubuntu1~910um1_all.deb -O /tmp/psb-kernel-source_4.41.2-0ubuntu1~910um1_all.deb
# dpkg -i /tmp/psb-kernel-source_4.41.2-0ubuntu1~910um1_all.deb
```

---

