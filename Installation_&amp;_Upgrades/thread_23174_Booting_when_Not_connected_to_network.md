---
title: "Booting when Not connected to network"
date: 2005-03-31
forum: Installation &amp; Upgrades
---

### Post by Recked on 2005-03-31
Hello,

Last night I loaded Hoary on my new laptop. I tried searching to find out if there is some way for Hoary to not look so long for a DHCP server when I am not connected to my network? I don't use wireless at all and have a wired network at home, but when booting it takes quite a bit longer for the OS to come up when I am disconnected from the network.

Also would like to once again congratulate the folks who put this together. I have switched over three machines now and am very pleased overall. You have much to be proud of.

thanks for any help....

---

### Post by alastair on 2005-03-31
DHCP is configured via :

/etc/dhcp3/dhclient.conf

If you look at the man page for this :

man dhclient.conf

There are some "timeout" type options. Perhaps worth an experiment.

---

