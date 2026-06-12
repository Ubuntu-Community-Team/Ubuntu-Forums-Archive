---
title: "Natty:  64-bit kernel on 32-bit userland?"
date: 2011-05-28
forum: Installation &amp; Upgrades
---

### Post by dsimcha on 2011-05-28
I'm trying to manually install a 64-bit kernel for 32-bit Ubuntu.  I have my reasons for doing so, but they're too complicated to explain here.  Prior to Natty, this worked fine.  Now, on Natty, I get the following error message when I try doing it the same way:

> 
dsimcha@dsimcha-laptop:~$ sudo dpkg -i --force-architecture linux-image-2.6.38-8-server_2.6.38-8.42_amd64.deb 
[sudo] password for dsimcha: 
dpkg: error processing linux-image-2.6.38-8-server_2.6.38-8.42_amd64.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 linux-image-2.6.38-8-server_2.6.38-8.42_amd64.deb
dsimcha@dsimcha-laptop:~$ cd Downloads/
dsimcha@dsimcha-laptop:~/Downloads$ sudo dpkg -i --force-architecture linux-image-2.6.38-8-server_2.6.38-8.42_amd64.deb 
dpkg: warning: overriding problem because --force enabled:
 package architecture (amd64) does not match system (i386)
(Reading database ... 159153 files and directories currently installed.)
Preparing to replace linux-image-2.6.38-8-server:amd64 2.6.38-8.42 (using linux-image-2.6.38-8-server_2.6.38-8.42_amd64.deb) ...
Done.
Unpacking replacement linux-image-2.6.38-8-server:amd64 ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.38-8-server /boot/vmlinuz-2.6.38-8-server
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.38-8-server /boot/vmlinuz-2.6.38-8-server
dpkg: dependency problems prevent configuration of linux-image-2.6.38-8-server:amd64:
 linux-image-2.6.38-8-server:amd64 depends on initramfs-tools (>= 0.36ubuntu6).
 linux-image-2.6.38-8-server:amd64 depends on coreutils | fileutils (>= 4.0); however:
  Package coreutils:amd64 is not installed.
 linux-image-2.6.38-8-server:amd64 depends on module-init-tools (>= 3.3-pre11-4ubuntu3); however:
 linux-image-2.6.38-8-server:amd64 depends on wireless-crda; however:
dpkg: error processing linux-image-2.6.38-8-server:amd64 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.38-8-server:amd64
When I try the dependencies manually, I get, for example:

> 
dsimcha@dsimcha-laptop:~/Downloads$ sudo dpkg -i --force-architecture coreutils_8.5-1ubuntu6_amd64.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (amd64) does not match system (i386)
dpkg: error processing coreutils_8.5-1ubuntu6_amd64.deb (--install):
 coreutils:amd64 8.5-1ubuntu6 (Multi-Arch: no) is not co-installable with coreutils:i386 8.5-1ubuntu6 (Multi-Arch: no) which is currently installed
Errors were encountered while processing:
 coreutils_8.5-1ubuntu6_amd64.deb
Has anyone had any success installing 64-bit kernels on 32-bit Natty?  If so, how can this be done?

---

