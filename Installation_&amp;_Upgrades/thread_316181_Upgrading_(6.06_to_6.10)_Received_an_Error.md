---
title: "Upgrading (6.06 to 6.10): Received an Error"
date: 2006-12-10
forum: Installation &amp; Upgrades
---

### Post by tarobs on 2006-12-10
[SIZE="3"]I was upgrading from Ubuntu 6.10 LTS to Ubuntu 6.10 by following the instructions from [here]("https://help.ubuntu.com/community/EdgyUpgrades#head-083dba9cd00350371c1a27ce7c1df6499c13828d"). I encountered an error that says:

Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz](http://ph.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)

What is wrong? What should I do?

[/SIZE]

---

### Post by tarobs on 2006-12-10
Here are some of the details of the error:

1. Here is the message from the terminal from the time I execute the gksu "update-manager -c" command up to the termination of the update:

:~$ gksu "update-manager -c"

(gksu:6544): Gdk-WARNING **: locale not supported by Xlib

(gksu:6544): Gdk-WARNING **: cannot set locale modifiers
(update-manager:6545): Gdk-WARNING **: locale not supported by Xlib

(update-manager:6545): Gdk-WARNING **: cannot set locale modifiers
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
extracting '/tmp/tmpH6X5-z/edgy.tar.gz'
authenticate '/tmp/tmpH6X5-z/edgy.tar.gz' against '/tmp/tmpH6X5-z/edgy.tar.gz.gpg'

(edgy:6545): Gdk-WARNING **: locale not supported by Xlib

(edgy:6545): Gdk-WARNING **: cannot set locale modifiers

:~$

2. Two windows popped out during the "Modifying the Software Channels" Step.

The first one popped out before the said step started:

**Third party sources disabled**

[I]Some third party entries in your sources.list were disabled. You can re-enable them after the upgrade with the 'software-properties' tool or with synaptic.
[/I]

The second one is the error message:

**Error during update**

*A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.*

Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz](http://ph.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)
---

Thanks in advanced for those who would help! :D

---

