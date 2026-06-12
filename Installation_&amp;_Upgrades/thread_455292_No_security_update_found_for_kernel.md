---
title: "No security update found for kernel"
date: 2007-05-26
forum: Installation &amp; Upgrades
---

### Post by txr13 on 2007-05-26
Pardon my newbishness, but I'm attempting to update the kernel in Feisty to the latest version that was announced in ubuntu-security-announce. The thing is, apt-get isn't locating it.

This is a server installation, command-line only. No packages are being held back by apt-get. It is finding and updating everything else as announced in the security mailing list, but not the kernel itself. Can anybody lend me a hand?

---

### Post by earobinson on 2007-05-26
Im pretty sure its going to install a new kernel, reboot your computer and do uname -a to check your kernel version

---

### Post by txr13 on 2007-05-26
No luck, it's still at 2.6.20-15-server. Worse, I also now can't log in via SSH. :(

---

### Post by txr13 on 2007-05-26
Okay, fixed the SSH issue by manually starting the daemon...how do I get it to start automatically on boot the way it should? :P

---

### Post by holli on 2007-05-26
Someone already filed a bug for the kernel issue: [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/117024](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/117024)

---

