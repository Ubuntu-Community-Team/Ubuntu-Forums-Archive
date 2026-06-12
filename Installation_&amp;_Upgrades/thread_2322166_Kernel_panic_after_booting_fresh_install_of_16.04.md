---
title: "Kernel panic after booting fresh install of 16.04"
date: 2016-04-26
forum: Installation &amp; Upgrades
---

### Post by fargoth on 2016-04-26
I had Ubuntu 15.10 running fine on my Thinkpad x200.

The live USB of 16.04 runs fine, ran a check on it's files - checks out ok.

Told the installer to format the ext4 drive and install 16.04 from scratch, everything seemed to go well up till after the restart - got a kernel panic right after the grub screen.

The error message during panic says /bin/sh exists but can not be executed.

I can execute that sh from the live USB though... (by going to the mount point of sda2, and executing it's /bin/sh)

Here's a [Boot-info summary]("http://paste2.org/DcvhzvjD").

Any ideas?

---

### Post by fargoth on 2016-04-27
It turns out this error is associated with a USB disk prepared using unetbootin for the 64bit version... 

Using Linux Live USB creator for the installation fixed it... I still wonder what was wrong, if someone has some insight into this.

---

