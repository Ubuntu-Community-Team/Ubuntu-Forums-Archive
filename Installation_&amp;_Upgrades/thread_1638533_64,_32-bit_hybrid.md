---
title: "64, 32-bit hybrid?"
date: 2010-12-05
forum: Installation &amp; Upgrades
---

### Post by dsimcha on 2010-12-05
I'm dual booting Windows 7 and Ubuntu on my laptop.  The laptop's CPU  does not support hardware virtualization.  I'm using VMWare Player to  allow use of my Linux partition (the same one that also runs on bare  metal) from within Windows.  Without hardware virtualization support,  this only works with 32-bit guests, so I have 32-bit Ubuntu installed.

  Occasionally, I need to run a 64-bit process under Linux and am  willing to reboot to do so.  I'd like to avoid having to maintain 3  separate partitions (64-bit Linux for bare metal, 32-bit Linux for  virtualization, Windows 7).  However, most of the time 32-bit Linux is  fine for me.

  Is there any reasonably simple way to install both a 64-bit and  32-bit kernel for the same Linux installation, have both kernels appear  in Grub, keep most of the userland 32-bit (except for libraries and development tools,  in which case I'd keep both versions installed) and allow 64-bit  processes to run if I boot the 64-bit kernel on the bare metal?   Ideally, I'd like to keep the default package repositories and any other  relevant default settings 32-bit even when running the 64-bit kernel.  However, I'd like to have access to 64-bit Apt.


  If this is not feasible, is there any other solution that wouldn't  require me to either maintain two Linux partitions or upgrade my  hardware?

---

### Post by dsimcha on 2010-12-05
Ok, I've gotten it mostly working by doing the following:

1.  Install a 64-bit kernel .deb.

2.  Install a bunch of 64-bit libraries from the 32-bit repo, such as []("http://packages.ubuntu.com/libc6-amd64")libc6-amd64 and lib64stdc++ and g++-multilib.

However, when I try to compile 64-bit C++ binaries, I get messages about missing c++config.h files.  These files exist in /usr/include/c++/4.4/<processor architecture>/bits.  Even after installing the 64-bit libraries, I only see i486 and i686 directories here.  On my system with a 64-bit install, I have an x64 directory.  Copying the files over from the i686 directory **seems **to work, but why doesn't installing lib64stdc++ and g++-multilib create such files?

---

