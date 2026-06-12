---
title: "Autotonomous (or 100% ssh) server install"
date: 2008-10-07
forum: Installation &amp; Upgrades
---

### Post by gep642 on 2008-10-07
I have a server (IBM x330) that I want to install linux on. The problem is, I have no kvm or null modem cable with which to interact with it.

This means I either need a linux install disk which boots and installs 100% on it's own, or one that starts up without interaction and has ssh by default. Any ideas?

Does Ubuntu server work like this?

---

### Post by cariboo on 2008-10-08
The Ubuntu server installation is an interactive process, you have to enter timezone, keyboard layout, partitions, username and password, and what packages to install. Have a look here:

[https://help.ubuntu.com/community/KickstartCompatibility](https://help.ubuntu.com/community/KickstartCompatibility)

This may be of some help.

Jim

---

### Post by cilkay on 2008-10-10
If you are already running some Linux distribution on your server and have a disk partition which you can use to bootstrap the process, you can install via [debootstrap]("https://wiki.ubuntu.com/DebootstrapChroot"). It works quite well but you have to be very careful to get it right the first time to avoid leaving your machine in an unbootable or unreachable via the network state. If you have a separate partition for swap, that is a good candidate for the partition you can use for bootstrapping.

I know that with lilo, you can specify which menu entry to boot for the next boot when you reboot and set an error timeout but I don't know if that is possible with GRUB. Collect all the information you can about network configuration so that you'll be able to get the network going on the first shot. Be advised that some hosting providers assign static IPs via DHCP and might expect some identifying string to be passed to the DHCP server.

---

