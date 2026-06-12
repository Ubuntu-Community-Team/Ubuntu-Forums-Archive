---
title: "Grub install error 15 'this is a fatal error'"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by mysterymann78 on 2008-07-04
A couple of weeks ago I downloaded Ubuntu to give it a whirl, and used the 'install inside windows' option, which installs the system like any other windows programme. Perfect to try it out since no disk partitioning and easy to remove if I didn't like it.

I did like it. It's fantastic, so I want a more permanent install with the view to phasing out windows vista over time.

I have created a new partition to install ubuntu to, and booted the computer from live usb stick. Clicked on 'install' and went through the process selecting the new partition to install to and the installation began.

At about 96% through the process an error message appears saying the grub could not be installed, error 15, 'this is a fatal error'.

I have tried to install several times now, each time selecting a different location to install the grub to each time, but with the same result everytime.

I can install ubuntu to the partition without installing grub, and that works fine. Unfortunately I can not then boot ubuntu.

Has anyone had same issue?

Is it possible to install grub from windows?

I have also tried using a windows prog called EasyBCD which lets you edit the mbr and add different OS but when I add ubuntu and point it at the correct partition and try to boot into ubuntu it only goes to 'grub>' prompt.

Any help greatly appreciated.

---

### Post by Pumalite on 2008-07-04
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)
Use Super Grub to fix it.
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

### Post by mysterymann78 on 2008-07-05
> **Pumalite said:**
> [http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)
Use Super Grub to fix it.
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

Super Grub didn't work. Came up with same 'error 15' message :-(

---

### Post by Pumalite on 2008-07-05
Post:
sudo fdisk -lu
(boot your Live CD)

---

### Post by ettercap on 2008-07-05
hey
even i had the exact same problem...
what i did is
went to the boot menu and installed 
LILO BOOT LOADER !!!!!

---

### Post by mysterymann78 on 2008-07-05
All working now, thanks for all your help. In the end it would appear that I managed to completely kill computer with Super Grub (don't ask how, I am jinxed!!)

In the end my computer stopped booting completely so I had to boot with liveCD. Decided to try a complete format of hard disk and then install Ubuntu, which worked without a hitch. I suspect that Windows have some sort of security in place to hinder people like me installing duel boot systems because they know that we will see  the light and abandon then.

Unfortunately I don't have Windows Vista anymore, probably not a bad thing but got rid of it sooner than I anticipated. Then again, it is better to rip plaster off quickly sometimes! 

Ubuntu does run sososososooooooooo much faster than Vista, even web browsing is faster.

Thanks again everyone.

---

