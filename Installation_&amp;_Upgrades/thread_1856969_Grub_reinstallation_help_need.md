---
title: "Grub reinstallation help need"
date: 2011-10-09
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2011-10-09
I am using ubuntu live cd.
I have install windows 7 a side with ubuntu 11.10.
Now i need to reinstall my grub.
1.ubuntu@ubuntu:~$ sudo grub
sudo: grub: command not found

bellow are some lines how can I continuous from here _

ubuntu@ubuntu:~$ sudo find / -name "*grub"
/boot/grub
/usr/sbin/update-grub
/usr/lib/grub
/usr/lib/grub-legacy/update-grub
/usr/lib/linux-boot-probes/mounted/40grub
/usr/share/grub
/usr/share/grub/default/grub
/usr/share/recovery-mode/options/grub
/var/lib/ucf/cache/:etc:default:grub
/etc/default/grub
/etc/alternatives/default.plymouth.grub
/etc/bash_completion.d/grub
/etc/kernel/postinst.d/zz-update-grub
/etc/kernel/postrm.d/zz-update-grub
/cdrom/boot/grub
/rofs/boot/grub
/rofs/etc/alternatives/default.plymouth.grub
/rofs/etc/bash_completion.d/grub
/rofs/etc/default/grub
/rofs/etc/kernel/postinst.d/zz-update-grub
/rofs/etc/kernel/postrm.d/zz-update-grub
/rofs/lib/partman/choose_method/45biosgrub
/rofs/lib/partman/init.d/50biosgrub
/rofs/lib/plymouth/themes/default.grub
/rofs/lib/plymouth/themes/ubuntu-logo/ubuntu-logo.grub
/rofs/usr/lib/grub
/rofs/usr/lib/grub-legacy/update-grub
/rofs/usr/lib/linux-boot-probes/mounted/40grub
/rofs/usr/sbin/update-grub
/rofs/usr/share/grub
/rofs/usr/share/grub/default/grub
/rofs/usr/share/recovery-mode/options/grub
/rofs/var/lib/ucf/cache/:etc:default:grub
/lib/partman/choose_method/45biosgrub
/lib/partman/init.d/50biosgrub
/lib/plymouth/themes/default.grub
/lib/plymouth/themes/ubuntu-logo/ubuntu-logo.grub
ubuntu@ubuntu:~$

---

### Post by retchid on 2011-10-09
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update && sudo apt-get install -y boot-repair && gksu boot-repair

Try the above from terminal

apparently small prog to repair grub

its in the forums somewhere

not entirely sure it works but did me no harm when i ran it

---

### Post by hoboy on 2011-10-09
> **retchid said:**
> sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update && sudo apt-get install -y boot-repair && gksu boot-repair

Try the above from terminal

apparently small prog to repair grub

its in the forums somewhere

not entirely sure it works but did me no harm when i ran it

Tks retchid
it has helped.

---

