---
title: "[SOLVED] What's the easiest way to dual boot Ubuntu &amp;amp; XP?"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by xpronic on 2007-11-07
The first time I installed the latest Ubuntu (7.10), it removed the XP boot loader despite me installing it in a different partition. :/

I've re-installed XP and this is how I've partitioned my HDD's:

[[IMG]http://img68.imageshack.us/img68/1754/mcwq6.th.jpg[/IMG]](http://img68.imageshack.us/my.php?image=mcwq6.jpg)


So as my title says - What's the easiest way to dual boot Ubuntu & XP? :confused:

---

### Post by Pumalite on 2007-11-07
Install XP first, then install Ubuntu and let Grub install to MBR.

---

### Post by tombott on 2007-11-07
As above post.
Ubuntu / Grub should detect your XP install and add it to the boot menu in Grub.

---

### Post by xpronic on 2007-11-07
XP is already installed, so I just did as I did before, but this time install this Grub program to Ubuntu and that's it?

---

### Post by Pumalite on 2007-11-07
Install Grub to MBR, that is (hd0), that is first partition of bootable hard drive, that means XP's MBR. You will have a Grub that will allow you to boot either OS.

---

### Post by ParanoiaPersonified on 2007-11-07
Grub should automatically be installed when you install Ubuntu. At least, that's what the documentation I've read suggests, and that's what happened when I installed Ubuntu.

---

### Post by tombott on 2007-11-07
It should just work mate.

---

### Post by aysiu on 2007-11-07
If you have at least 1 GB of RAM, I wouldn't even bother with a dual boot. I'd just use the .ISO or CD and install Ubuntu on a virtual machine in Windows using VirtualBox.

---

### Post by xpronic on 2007-11-08
OK I have re-installed Ubuntu and this time it installed the Grub program. I restarted the PC and it now gives me the option to select the OS I want to boot. 

Thanks for all the help! :KS

---

