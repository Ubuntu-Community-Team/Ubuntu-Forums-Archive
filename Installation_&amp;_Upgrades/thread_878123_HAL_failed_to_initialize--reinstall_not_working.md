---
title: "HAL failed to initialize--reinstall not working"
date: 2008-08-02
forum: Installation &amp; Upgrades
---

### Post by CaptainPants on 2008-08-02
Hi,

I recently updated to the latest version of Ubuntu and ever since then whenever I log in I get a message that says "HAL failed to intitialize."  And as you can probably guess, I cannot use flash drives or CDs/DVDs.

I found a couple threads around here about HAL and everybody else seemed to get it working with a reinstall, but when I tried to reinstall using the synaptic package manager I got this message.

[INDENT]Setting up hal (0.5.9.1-6ubuntu5) ...
 * Reloading system message bus config...
   ...done.
 * Starting Hardware abstraction layer hald
invoke-rc.d: initscript hal, action "start" failed.
dpkg: error processing hal (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 hal
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up hal (0.5.9.1-6ubuntu5) ...
 * Reloading system message bus config...
   ...done.
 * Starting Hardware abstraction layer hald
invoke-rc.d: initscript hal, action "start" failed.
dpkg: error processing hal (--configure):
 subprocess post-installation script returned error exit status 1
[/INDENT]

Could somebody point me in the right direction?

Thanks.

---

