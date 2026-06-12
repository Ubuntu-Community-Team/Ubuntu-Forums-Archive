---
title: "base-config screws up installation!"
date: 2005-09-08
forum: Installation &amp; Upgrades
---

### Post by ispmarin on 2005-09-08
Hello all. 
I have installed Ubuntu Hoary on a Compaq Prosignia 162 after a long struggle. The problem was, like I posted here, that the framebuffer gave me problems. On boot, no problem: I used the debian-installer/framebuffer=off option, and the instalation worked well. But, after the first reboot, the installer tries to run the base-config after the installation. The base-config uses framebuffer! And there is no option to not use framebuffer on base-config that I know. So, I had to use the recovery mode, install all the packages by myself, and after a loooong time, foudn in /etc/inittab the base-config autorun line. I removed the line, and the system boots!

Please, tell me if there is a way to desabilitate the base-config framebuffer, or if there is something else that the base-config does after the installation.

Thanks.

Ivan

---

