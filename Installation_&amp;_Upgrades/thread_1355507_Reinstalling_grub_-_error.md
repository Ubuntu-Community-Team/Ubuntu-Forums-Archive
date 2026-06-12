---
title: "Reinstalling grub - error"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by celtic426 on 2009-12-15
***Edit: Solved, read second post.



Hi, I am following these steps to restore grub after installing windows 7: 

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD]("http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD")


When I attempt to give the command, 

sudo grub-setup -d /media/Ubuntu910/boot/grub -m /media/Ubuntu910/boot/grub/device.map /dev/sda

i get this error: 

error: cannot open `/dev/sdb' while attempting to get disk size


Can someone please help?  I'm not sure what to do.

Here's my Gparted screenshot:
[IMG]http://img34.imageshack.us/img34/9679/imagecza.png[/IMG]


sda1 is WinXP
sda3 is Win7
sda5 is storage
sda8 is Ubuntu910

Thanks!

---

### Post by celtic426 on 2009-12-15
Despite the error, grub was still installed and working upon reboot.  So no problem.  I should have known that sdb was a different hard drive and not pertinent to the situation.

---

