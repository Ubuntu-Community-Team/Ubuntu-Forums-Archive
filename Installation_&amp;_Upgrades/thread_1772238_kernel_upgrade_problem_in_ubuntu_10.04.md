---
title: "kernel upgrade problem in ubuntu 10.04"
date: 2011-05-31
forum: Installation &amp; Upgrades
---

### Post by sharp777 on 2011-05-31
Hello. I have an ubuntu 10.04 server as a samba BDC domain controller and today I have installed a kernel 2.6.32-32-generic-pae from apt-get. Kernel installed sucsessfully, but after reboot I'd have a kernel panic with message:
Kernel panic: Unable to mount root fs on unknown-block (0,0)
I have rebooted and tried to boot new kernel by hand, and I found some interesting thing. When I load linux kernel by command: linux /vmlinuz-2.6.32-32-generic-pae , name of initrd image is changed! It became initrd.img-2.6.32-32-generic-pae.. , with 2 dots at the end. I have added a test menuentry to grub with new name of initrd and kernel loaded sucsessfully. I have a question: what is a dots and is this a bug or feature? And how to add new name to grub.cfg permanently?

---

