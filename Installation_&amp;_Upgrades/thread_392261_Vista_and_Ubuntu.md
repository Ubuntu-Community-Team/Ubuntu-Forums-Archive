---
title: "Vista and Ubuntu"
date: 2007-03-24
forum: Installation &amp; Upgrades
---

### Post by Voltaic Shock on 2007-03-24
I currently have Vista installed.

I have two HD in my desktop.  One is 250GB and the other is 80GB.  I want to install Ubuntu on my 80GB HD.  Windows won't recognize the 80GB drive but Ubuntu live CD does fine.  I have read bad things about Vista and dual boot.  I won't need to partition the Vista drive since I have two HD.

The second HD is on a IDE controller.

I have done this before with XP, but not sure how it will work with Vista.

The main question is will I have problems getting back into Vista after I install Ubuntu on the second HD?

Thanks for the help.

---

### Post by seshomaru samma on 2007-03-24
When you install Ubuntu you install a boot menu called Grub  . Grub will allow you to choose either Vista or Ubuntu when you boot.
Sometimes Grub doesn't recognise Visat , this is easy to solve , there are many posts about it here , just use the search function in the forum.
Good Luck

---

### Post by bulldog on 2007-03-24
Or just install GRUB on the hdd with ubuntu and leave your Vista untouched.
Only thing is you'll have to change your boot device when you want to boot ubuntu or Vista in your BIOS,unless you have an option which device you want to boot during start-up.

---

### Post by Voltaic Shock on 2007-03-24
Thanks for the replies.

I plan to install Ubuntu only on the 80GB HD and leave Vista alone, but I would still like Vista to be the first option.

My wife still uses the desktop and for now it would be best to start up with Vista first.  I could just do as you say and tell it to boot from the first HD and then I can choose it myself when I want to go into Vista.

---

### Post by seshomaru samma on 2007-03-24
you can set grub to boot into vista by default
the only problem is that if ever you wanted to get rid of ubuntu -you'll have to rewrite the MBR. with XP you just needed the install CD and run 'fixmbr' but Vista has a different boatloader and it might not be that easy.

---

### Post by ssican on 2007-03-25
First, it is necessary to know, if the HDs are SATA or IDE(PATA). This links are just an option to install Ubuntu: [http://wiki.gtwy.net/index.php/Dual_Boot_Vista_and_Linux](http://wiki.gtwy.net/index.php/Dual_Boot_Vista_and_Linux) and [http://www.ehomeupgrade.com/entry/2622/how-to_dual-boot_ubuntu](http://www.ehomeupgrade.com/entry/2622/how-to_dual-boot_ubuntu)  This last link have a method similar with the first link
Other important link is GRUB Page: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

EDIT: See also this forum: Dualboot Two Hard Drives  [http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

