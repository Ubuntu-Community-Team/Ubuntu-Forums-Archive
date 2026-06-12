---
title: "xml2-config not found"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by sshahir on 2007-10-24
Hello ,

After installing Apache http Server 2.2.6, I tried to install PHP server 5.2.4; however, I am runing into installation error:

[COLOR="Red"]
error: xml2-config not found. Please check your libxml2 installation.[/COLOR]

Based on the [[COLOR="Blue"]thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=389919&hi ghlight=PHP+xml2-config") to work-around the issue, the libxml2-dev package has to be installed.

Therefore, I downloaded the libxml2-dev package, but when I try to install the package, package installer is thrown the error below(please see the attachement).

[COLOR="Red"]Error: Dependency is not satisfiable: libxml2[/COLOR]

First time when I had encountered the error message during installing the libxml2-dev,I checked my synaptic manager and libxml2 was already installed. I re-installed the libxml2 package which causes the package broken:(. After installing the libxml2 package, my Ubuntu OS is cashed:oops:, and I had to format the partitions and reinstall the OS:mad:.

Now after reinsalling the ubuntu OS 6.0.6 and Apache http Server 2.2.6, I am runing to the same error during the PHP server 5.2.4 installation.

[COLOR="Red"]error: xml2-config not found. Please check your libxml2 installation.[/COLOR]

To work-arond the error, I am trying to insall the libxml2-dev package, and thepackage installer is thrown the same error:

[COLOR="Red"]Error: Dependency is not satisfiable: libxml2[/COLOR]

At this point, the following three questions come to my mind.

[COLOR="DarkRed"]   1.      How to install xml2-config?
   2.      Is the installation of the libxml2-dev package the right solution to work-around the PHP installation error?
   3.      If it is, please let me know how should I install the libxml2-dev package without runing into the " Dependency is not satisfiable: libxml2" error message?[/COLOR]

I appreciate for any answers, comments, or solutions.


sshahir

---

### Post by sshahir on 2007-10-25
Any suggestions?

---

