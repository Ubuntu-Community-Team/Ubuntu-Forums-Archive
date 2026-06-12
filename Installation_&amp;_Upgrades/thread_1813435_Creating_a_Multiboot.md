---
title: "Creating a Multiboot"
date: 2011-07-27
forum: Installation &amp; Upgrades
---

### Post by silveringking on 2011-07-27
Hi, here is my problem I was trying to make a multiboot between windows 7 and Natty... I installed both, but the only way I can make the other working is by using super f-disk and activate the other disk... I heard that Grub or Lilo could do that, but I do not seem to be able to do it... Can you guys help me by giving me a link to a tutorial? Thank you!

Ps: I am using the Super Ubuntu extension...

---

### Post by Mark Phelps on 2011-07-27
If you have only one physical drive, when you installed Ubuntu (to its own partition), it would have installed GRUB (its boot loader) and you would then have been able to boot into a menu and choose Windows or Ubuntu.

If you installed inside Win7 using Wubi, it would have modified the Win7 boot loader menu to add an entry for Ubuntu.

Either way, you should be getting a selection menu when you boot.

If you have two physical drives, with Win7 on one and Ubuntu on the other, you need to boot from the Ubuntu drive.  If you can do that, once in Ubuntu, open a terminal and enter "sudo update-grub".  That will regenerate the GRUB menu and when you reboot, you should get a menu with OS selections including Windows 7 and Ubuntu.

---

### Post by tommcd on 2011-07-28
> **silveringking said:**
> Can you guys help me by giving me a link to a tutorial? Thank you!

Here are detailed tutorials for dual booting Windows7 with Ubuntu: [http://members.iinet.net.au/~herman546/](http://members.iinet.net.au/~herman546/)

---

