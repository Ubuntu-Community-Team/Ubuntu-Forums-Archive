---
title: "Restore ubuntu"
date: 2012-10-12
forum: Installation &amp; Upgrades
---

### Post by nadirhajiyev on 2012-10-12
Hey guys.
I`m newbie on Ubuntu.
Is there ant command to restore all of the system, to uninstall all installed software, to remove all pathes, etc.
Thanks.

---

### Post by oldfred on 2012-10-14
Welcome to the forums.

What is it your want to do? You can often make repairs from liveCD or chroot (CHange ROOT) using kernel of liveCD to make repairs of your install.

If you want to do a clean install, you can backup /home including the hidden USER settings and restore /home to have your data back.

If you want to repair booting.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.


[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)

Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

