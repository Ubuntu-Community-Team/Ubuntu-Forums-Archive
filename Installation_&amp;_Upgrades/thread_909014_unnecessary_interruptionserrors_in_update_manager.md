---
title: "unnecessary interruptions/errors in update manager"
date: 2008-09-03
forum: Installation &amp; Upgrades
---

### Post by tfylling on 2008-09-03
In order to not screw up my Qt libraries for a program I'm dependent on at work, I uncheck the upgrade of nas when running the update manager, however the update manager seems to be completely ignorant of why a component wasn't installed, since it during the download phase will pop an error box with the message "E: nas: subprocess post-installation script returned error exit status 127".

After closing that it feels the need to tell me again, this time with a terminal window saying

[snip]
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up nas (1.9-1.el4) ...
/var/lib/dpkg/info/nas.postinst: 3: /sbin/chkconfig: not found
dpkg: error processing nas (--configure):
 subprocess post-installation script returned error exit status 127
[snip]

I already know you can't install it! I bloody well told you not to! :mad:

Is there any way to prevent the update manager interrupting in the middle of the update process for these nonsense errors? Since it's right at the end/after the download phase it means that for large updates I can't just start it, go for a coffee and come back to an updated system.

Alternatively, can I prevent nas from showing up in the update manager so I don't even have to uncheck it every time? If so, please also include how I can add it again when the problem with Qt is eventually resolved, if this is not a simple matter of reversal...

Thank you.

Edit:
Should probably say that I'm running Hardy 64 bit.

---

### Post by tfylling on 2009-02-11
Suddenly remembered this post and figured I should close it.

The error was caused by a post-install script in the original rpm which I converted with alien and stupidly used the -c option. I also found the lock version choice in synaptic, but it would still be an idea, imo, if it was possible to lock version from the update manager as well, since that is where you'll encounter the problem.

---

