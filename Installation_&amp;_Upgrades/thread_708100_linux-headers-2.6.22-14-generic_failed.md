---
title: "linux-headers-2.6.22-14-generic failed"
date: 2008-02-26
forum: Installation &amp; Upgrades
---

### Post by Jonathan23 on 2008-02-26
I used the update manager gui and had a problem installing the update linux-headers-2.6.22-14-generic. After it failed initially, I had to go through some steps to get my machine to boot properly and get my graphics card drivers to work properly. My machine is running now, but the update still will not install and when I try to install other updates through the update manager or packages through synaptic I get messages like "E: /var/cache/apt/archives/linux-headers-2.6.22-14-generic_2.6.22-14.52_i386.deb: failed in buffer_read(fd)" Any tips?

---

### Post by Partyboi2 on 2008-02-26
You could try [this]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=565037")

---

### Post by Jonathan23 on 2008-02-27
Good thought, but it didn't work. I removed the package from /var/cache/apt/archives tried running apt-get upgrade again and came back with the same error on the linux header update. I still can't install new software through synaptic nor can I get any updates through the update manager.

---

