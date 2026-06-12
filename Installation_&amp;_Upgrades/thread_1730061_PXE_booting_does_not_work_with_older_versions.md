---
title: "PXE booting does not work with older versions"
date: 2011-04-15
forum: Installation &amp; Upgrades
---

### Post by Burillo on 2011-04-15
Hi all

I have set up a DHCP server with TFTP. Whenever i download maverick netboot release the machine boots fine. When i download older netboot files (from, say, hardy), the remote machine can't boot, saying that my TFTP server does not support tsize option (it does, and this option is set in config file, and besides, maverick boots fine).

Why do i need older releases? The problem is that during the installation (actually during hardware detection part) the machine gets kernel panic (not maverick-specific, happens on any modern distro, including recent SuSE and Debian). I was able to install older SuSE (10.something) in the past, so it must be something in the newer kernels that prevents it from installing. So i was trying to download older ubuntu releases to try and boot it, but neither lucid nor hardy (trying out karmic) cannot boot from the files provided in netboot directory on ubuntu's FTP.

From the output on the screen i can judge that PXELINUX itself boots quite happily but for some reason either cannot boot further, or cannot read configuration, or whatever.

Any ideas?

---

### Post by Burillo on 2011-04-16
up

---

### Post by Burillo on 2011-04-18
up

---

