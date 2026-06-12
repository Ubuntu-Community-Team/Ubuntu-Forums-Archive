---
title: "Karmic beta broke wireless and wired internet"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by patmalcolm91 on 2009-10-04
Hi,

I recently upgraded from jaunty to karmic beta via update-manager. After the upgrade I found that I get error messages on boot that say:

iwlagn: MAC is in deep sleep!

Once I'm logged in, network-manager says "no devices found" and I can't even connect to a wired network.

I tried wicd, and it shows a wired network but says it fails in getting an ip address.
Ifconfig only shows the loopback device.

I've installed karmic-backports as suggested by another thread but this doesn't help. I also tried installing kernel 2.6.32 but still no success.

My card is the intel wireless WiFi Link 5100 and my ethernet controller is the Atheros AR8121/AR8113/AR8114 PCI-E (rev b0). These show up in the output of lspci.

Can anyone help? Thanks.

Patrick

P.s. The way I've been installing packages is by downloading .deb files to my flash drive on a public computer.


EDIT: I've now found a workaround that setting acpi=off in my kernel boot line makes internet work. I believe this bug is my problem: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418933?comments=all]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418933?comments=all")

---

