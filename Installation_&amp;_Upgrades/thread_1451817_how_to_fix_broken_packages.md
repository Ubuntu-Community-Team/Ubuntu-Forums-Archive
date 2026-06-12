---
title: "how to fix broken packages?"
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by lesterness on 2010-04-11
I have a broken package and can't seem to fix it.  Now, nothing can be downloaded from synaptic.  I get the following error message:

Processing triggers for software-center ...
Setting up courier-mta (0.61.2-lubuntu3) ...
 * Starting Courier mail server...
 * Starting Courier mail server...
invoke-rc.d: initscript courier-mta, action "start" failed.
dpkg: error processing courier-mta (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 courier-mta
E: Sub-process /usr/bin/dpkg returned an error code (1)


How do I fix this?

Thanks.

Lesterness

---

### Post by lesterness on 2010-04-11
> **lesterness said:**
> I have a broken package and can't seem to fix it.  Now, nothing can be downloaded from synaptic.  I get the following error message:

Processing triggers for software-center ...
Setting up courier-mta (0.61.2-lubuntu3) ...
 * Starting Courier mail server...
 * Starting Courier mail server...
invoke-rc.d: initscript courier-mta, action "start" failed.
dpkg: error processing courier-mta (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 courier-mta
E: Sub-process /usr/bin/dpkg returned an error code (1)

How do I fix this?

Thanks.

Lesterness

Problem solved!  I looked up the error message "dpkg: error processing courier-mta (--configure):" in Ubuntu's documentation on line.  Community documentation suggested I re-install Postfix, with 
SUDO APTITUDE INSTALL POSTFIX, and accept the defaults. It works! I didn't re-configure.

---

