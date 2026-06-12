---
title: "adding other distro on seperate partition to grub"
date: 2007-02-15
forum: Installation &amp; Upgrades
---

### Post by FreakTech on 2007-02-15
I recently installed PClinux on another partition of my hard drive.   I thought I new how to add it to the grub but when I did I can't boot into it.  It gives me xorg error and will not boot.  I am able to boot in Ubuntu fine.  Can anyone help me?

---

### Post by louis_nichols on 2007-02-15
If you receive an xorg error, it means it's probably not a GRUB problem. It seems to pass that point.

---

### Post by FreakTech on 2007-02-15
Yeah that's what I thought.  When I installed PClinux it replaced my current Grub with it's install.  I was able to load it then but could not get into Ubuntu which is my primary.  I reinstalled the Ubuntu Grub from the live CD not I am getting the xorg error.

---

### Post by louis_nichols on 2007-02-15
OK. I understand that. It could be some kernel parameter that PCLinux needs in grub.

Can you post here the exact text of the xorg error? We can start troubleshooting from there.

Another suggestion is to boot Ubuntu then read the file /boot/grub/menu.lst from the PCLinux partition and see exactly the kernel parameters PCLinux needs, then add them to the corresponding line in the file /boot/grub/menu.lst under the Ubuntu partition.

---

### Post by FreakTech on 2007-02-15
I am currently at my office and don't have my laptop with me.  When I get home tonight I will post the out put of the xorg error.  Thanks again for your help

---

