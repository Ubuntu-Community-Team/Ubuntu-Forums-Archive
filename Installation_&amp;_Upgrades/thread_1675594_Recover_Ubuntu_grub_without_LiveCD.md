---
title: "Recover Ubuntu grub without LiveCD"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by paulocoghi on 2011-01-25
I installed Windows after installing Ubuntu. But Ubuntu is still intact in its partition.

I'm trying to run the Ubuntu LiveCD to recover grub, but the LiveCD no longer works. It stops the boot process and does not load completely.

I can not run Ubuntu in live mode to recover grub.

Is there any way to recover the grub/grub2 without the LiveCD?

---

### Post by sikander3786 on 2011-01-25
First of all, I hope it is not a Wubi install and Ubuntu is installed on its own separate partition (??).

You can use the Super Grub Disk, Rescatux for Grub2.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Or you can choose to live with a Windows based Ubuntu bootloader, EasyBCD.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

But remember, Grub2 is a far better choice.

Or if you've got the Ubuntu image on your computer, you can try burning a USB and boot from that.

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

Or, diagnose why the Live CD is not working. I suspect the disc is defected. Press any key as soon as the computer starts booting from the disc and you'll see the Main page options. Choose, "Check disc for defects".

If the disc is defected, try burning a new disc at the lowest possible speeds.

---

### Post by mikewhatever on 2011-01-25
...long story short, you'll need a live cd.:P

---

