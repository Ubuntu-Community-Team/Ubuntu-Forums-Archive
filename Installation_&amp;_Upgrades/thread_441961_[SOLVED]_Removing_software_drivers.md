---
title: "[SOLVED] Removing software drivers"
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by IanB2 on 2007-05-13
I hope you can help. I am completely new to Linux.

I have bought and successfully run a USB adapter (had to use command line and follow instructions to install the drivers, but I must confess I don't know what I'm doing).

I seem to have 'broken the software installation' by accidentially re-running the install script for the adapter. (I was sent an updated script for the device as there have been problems with the latest release of Ubuntu)

I now have two devices listed in Network Tools 
- Unknown Device (rausb0) *with alpha numeric IP address (this used to be the only entry with an numeric IP address when it worked!)*
- Unknown Device (rausb0.avahi) *with IP address 169.254.5.100*

I think the two settings are conflicting and the question is '**How do I remove these drivers so I can start again?**' There doesn't appear to be a graphical way of doing this and the help files rely on having internet access.

I really don't want to break the system further by 'blundering around' and would appreciate any pointers.

---

### Post by IanB2 on 2007-05-14
Problem solved by the developer ...... the avahi tool was interfering with the USB adapter set up.

The avahi process runs in the background and tries to detect new access points and interface connections.

---

