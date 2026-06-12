---
title: "Reboot install hang, different problem"
date: 2006-08-31
forum: Installation &amp; Upgrades
---

### Post by mrcamuti on 2006-08-31
Howdy all,
I am installing Breezy Badger on a Dell Inspiron 3000 laptop (brace yourselves: 200 MHz P1, 48 megs of RAM, and a 2.2 GB HDD. Sweet, I know.)
Before you ask, Xubuntu would have nothing to do with this machine, couldn't get it to do much of anything other than gripe.
FreeBSD installed and ran fine, but I would like something prettier to interact with for the kitchen table internet laptop that this will be.

OK, so the problem lies in that when 'Package Install' begins, it hangs at 'Preparing to install...'

Alt-F4 reveals that the shell (usage correct here?) reads:
Reading package lists...
Building dependency tree...
The following NEW packages will be installed:
xresprobe
/usr/bin/tail: /var/log/base-config-pkgsel.log: file truncated

And then it just stalls here. Let it sit overnight, no change.



ALSO, as a side note, the sychronization clock at ntp.ubuntulinux.org fails, but rest of bootup is seamless.

Any suggestions / pearls of wisdom greatly appreciated.

Oh, and installed using the suggestion in a wiki thread of Breezy with following boot options:
server noapci pci=noapci nolapic noapic nodma hdc=cdrom hdc=noprobe


Thanks in advance.

---

