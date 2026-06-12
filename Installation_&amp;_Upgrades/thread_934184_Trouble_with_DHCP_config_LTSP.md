---
title: "Trouble with DHCP config LTSP"
date: 2008-09-30
forum: Installation &amp; Upgrades
---

### Post by trboyden on 2008-09-30
I am attempting to setup an Ubuntu 8.04.1 LTSP test environment on our network that already contains a DNS server run by our parent company that we have no control over.

I have configured the client by MAC address with a static IP in the dhcpd.conf file. The client initially connects to the LTSP DHCP server, loads pxelinux.cfg/default, then loads vmlinuz, then initrd.img, says ready, then Loading, please wait and then does another DHCP request. It then errors out and boots to Busy Box. Performing a Ctrl-Alt-F1 shows that the client made a second DHCP request to the corporate DHCP server which it can't get the Ubuntu file system from.

What config file controls the network settings for this second DHCP request by the client at this point in the boot process?

I looked at dhclient.conf, as that has options to reject a DHCP server, but it had no effect on the boot up process.

Thoughts?

---

