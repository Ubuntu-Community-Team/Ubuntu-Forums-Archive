---
title: "unable to install 9.10 beta on ESXi"
date: 2009-10-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sweberzerk2 on 2009-10-20
Hi,

I have tried to install 9.10 beta (server version) on a ESXi virtual machine. The actual installation succeeds but after reboot it chokes when trying to do something with apparmor. 

Begin: Running /scripts/init-bottom ...
Begin: Starting AppArmor profiles ...
chroot: cannot execute /etc/apparmor/initramfs: Exec format error
Failure: AppArmor profiles failed to load
Done.
[    8.297067] request_module: runaway loop modprobe binfmt-0000
[    8.297170] request_module: runaway loop modprobe binfmt-0000
[    8.297528] request_module: runaway loop modprobe binfmt-0000
[    8.297631] request_module: runaway loop modprobe binfmt-0000
[    8.298238] request_module: runaway loop modprobe binfmt-0000
and after that it hangs for a while and then crashes.

I have successfully installed exactly the same on a workstation vm. I am new to ESXi so I thought I messed something up there but after installing 9.04 without problems I now think it has something to do with the 9.10 system. 
Any ideas about how to resolve this?

---

