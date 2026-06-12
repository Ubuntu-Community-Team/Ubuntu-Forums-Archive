---
title: "Failed Alternate Install"
date: 2007-02-01
forum: Installation &amp; Upgrades
---

### Post by Priswell on 2007-02-01
I'm trying to install Ubuntu using the Alternate Install Disk.

During the installation of the kernel, it reached 83%, considered all its options for many, many minutes and then gave this error message:

Unable to install the selected kernel

An error was returned while trying to install the kernel into the target system.

Kernel Package 'linux-386'

Check /var/log/syslog or see virtual console 4 for the details

What does thie error message mean, and how do I proceed from here?

---

### Post by glabouni on 2007-02-01
have you checked var/log/syslog ? what does it say ? 

ctrl+alt+f4 to get to virtual console 4

---

### Post by Priswell on 2007-02-01
When I hit ctrl+alt+f4 I found the following:

A screenful of:

Feb 1 10:27:17 dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67

---

