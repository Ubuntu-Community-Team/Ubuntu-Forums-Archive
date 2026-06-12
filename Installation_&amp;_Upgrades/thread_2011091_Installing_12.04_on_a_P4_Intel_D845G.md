---
title: "Installing 12.04 on a P4 Intel D845G"
date: 2012-06-26
forum: Installation &amp; Upgrades
---

### Post by dbclinton on 2012-06-26
I'm trying to install 12.04 on an Intel P4 (Intel D845Gvsr) with 500MB RAM that always happily booted to 10.04. The computer reads the DVD and appears to launch the live session when I request it, but within seconds the screen goes black and that's the end. I've also tried booting the machine as a thin Client to my Edubuntu 12.04 server (which has other clients successfully booting). My server's DHCP gave the client an ip address, but the screen then goes blank. Syslog from the server gives me this:

Jun 25 21:23:22 dbclinton dhcpd: DHCPACK on 192.168.0.21 to 00:0c:f1:90:74:c6 via eth1 Jun 25 21:23:22 dbclinton in.tftpd[29868]: tftp: client does not accept options

I figured it was a video problem so, through BIOS, I tried both the integrated and AGP (Radeon 9200 pro) controllers - with no improvement.

Any ideas?

Thanks,

---

