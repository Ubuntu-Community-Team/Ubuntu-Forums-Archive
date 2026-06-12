---
title: "Lost all network interfaces after upgrade to 9.10"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by acidbits on 2009-10-14
I've just upgraded to 9.10 and all network interfaces (eth0 & wlan0) have gone :-/

It's a laptop, lspci says: 

Ethernet Controller: Marvell 88E8040T
Network Controller: Intel wireless wifi link 5100

sudo ifconfig eth0 up

"... no such device"

I have to fix this manually, no network connection at all, can't apt-get update/upgrade :-(

Any hint?

Thanks in advance

---

### Post by RobtA on 2009-10-14
Try this: Open Terminal, and attempt to launch the network manager program.

nm-connection-editor

If it fails, and complains that some file is missing, or some folder cannot be opened, then you may be able to repair the problem manually. That happened to me: 9.10 was working fine on wireless until some update had an "oops," and I repaired it by creating a dummy file or folder according to Terminal's complaint. The "oops" went away at the next update, so not many folks saw it.

---

### Post by acidbits on 2009-10-15
Nothing to do with networkmanager. I've seen it's already at bugs.launchpad:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/407824](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/407824)

---

