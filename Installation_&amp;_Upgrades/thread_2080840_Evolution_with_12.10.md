---
title: "Evolution with 12.10"
date: 2012-11-05
forum: Installation &amp; Upgrades
---

### Post by Frankiewizard on 2012-11-05
Evolution calender when installing I get "Package installation failed".
Is there something I can do ?

Compaq Presairo CQ 62 "64 bits"

---

### Post by Frankiewizard on 2012-11-05
When I try to install it from the terminal I get this.

[HTML]dpkg: error processing libbonoboui2-0:amd64 (--configure):
 package libbonoboui2-0:amd64 is not ready for configuration
 cannot configure (current status `half-installed')
dpkg: dependency problems prevent configuration of libgnomeui-0:amd64:
 libgnomeui-0:amd64 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0:amd64 is not installed.

dpkg: error processing libgnomeui-0:amd64 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libbonoboui2-0:amd64
 libgnomeui-0:amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)
frankiewizard@frankiewizard-Presario-CQ62-Notebook-PC:~$[/HTML]

---

### Post by dluco on 2013-04-21
Have you tried updating your system before the installation?
Also, does the installation fail with the terminal as well as the Software Centre?

---

