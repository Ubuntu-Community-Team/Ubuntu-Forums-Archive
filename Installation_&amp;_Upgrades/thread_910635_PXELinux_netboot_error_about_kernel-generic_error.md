---
title: "PXELinux netboot error about kernel-generic error"
date: 2008-09-04
forum: Installation &amp; Upgrades
---

### Post by thesheff17 on 2008-09-04
I'm trying to build a box that does automatic installs of ubuntu 8.04 I386 server for my company.

So I have this:
mount /media/cdrom
cp -a /media/cdrom/install/netboot/* /var/lib/tftpboot/

and I edit the /var/lib/tftpboot/pxelinux.cfg/default and point it to my preseed.cfg file.

But I get this everytime:

An error was returned while trying to install the kernel into the target system. 

Kernel package: 'linux-generic'.

Check /var/log/syslog or see virtual console 4 for details.

under console 4:
The following packes have unmet dependencies:
linux-generic: Depends: linux-image-generic (= 2.6.24.19.21) but it is not going to be installed.

I'm not sure why I get this problem if I'm getting both the netboot.tar.gz from the cdrom and I'm trying to install off that cd-rom image.

Please help :) greatly appreciated in advice

---

### Post by thesheff17 on 2008-09-08
This was because I was using an old 8.04 ISO that I burned right when it came out.  I needed to get the lastest 8.04.1 disk and used it and it worked like a charm.  Well there are other issues and I need repost them.

1) 8.04 Server has mysql server installed by default and my preseed.cfg doesn't contain entries for hitting enter when the menu comes up
2) I am getting these weird stars when I type in the console. Not sure what that is prob something wrong with the keyboard entries but I will continue to look.

---

