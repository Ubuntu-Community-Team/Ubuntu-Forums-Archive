---
title: "How to boot from iSCSI disk"
date: 2016-04-20
forum: Installation &amp; Upgrades
---

### Post by maorui on 2016-04-20
I have a server with no harddisk, but attached an iSCSI disk. I installed the Ubuntu 14.04-4 to the iSCSI disk successfully. But the bootup process stoped somewhere. From the screen output, it seems the NIC could not get IP address from DHCP. But actually I specified the IP in the installation. I wonder if the network link to the iSCSI server was broken because of the missed IP problem, and caused system disk missed too.

What can I do to fix this?

The attachment is the last screen.

---

### Post by maorui on 2016-04-22
Found the reason, the server had two NICs, but only one connected. After connected both, the problem was gone. Might be a bug?

---

