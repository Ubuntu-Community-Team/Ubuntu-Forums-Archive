---
title: "Ubuntu 8.04 not Working! :("
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by nemesis93 on 2008-06-12
So I installed Ubuntu 8.04 hardy heron and I used the wubi installer inside of windows after i finished the installation it told me take out the cd and reboot. I took out the CD and rebooted my machine. After that i get the screen which asks me to pick the operating system to start:
Microsoft Windows XP Home Edition
Microsoft Windows Recovery Console
Ubuntu
I picked Ubuntu.

After loading for about 15-20 seconds Ubuntu stops loading at almost the third bar to the left and just stays their for a **LONG WHILE**(about 8 min!!!).It stays at the same thing almost the third bar and it shows me this Note: The error is under Loading hardware drivers
_Error Message:_
*Loading hardware drivers...                                       
/etc/rcS.d/S10udev: 105: usplash_write: not found
/etc/rcS.d/S10udev: 105: /usr/bin/tput: not found
/etc/rcS.d/S10udev: 1: usplash_write: not found
/etc/init.d/rc: 317: usplash_write: not found
/etc/init.d/rc: 317: sed: not found
init: rcS main process (6222) killed by SEGV signal
init: Unable to execute "/bin/sh" for rc-default: No such file or directory
init: rc-default main process (7535) terminated with status 255

My Specs:
HP Pavilion a820n ( detailed specs at this location: [http://h10025.www1.hp.com/ewfrf/wc/product?product=443070&lc=en&cc=us&dlc=en&lang=en&cc=us](http://h10025.www1.hp.com/ewfrf/wc/product?product=443070&lc=en&cc=us&dlc=en&lang=en&cc=us))
Intel Pentium 4 3.20 ghz HT
1 GB DDR PC3200
Microsoft Windows XP Home Service Pack 2
ATI Radeon X1550 PCI (not PCI-Express)
200 GB SATA Internal Hard Drive
250 GB Seagate SATA External Hard Drive

One more little thing that i observed:
When i run this same version of Ubuntu under Vmware or Microsoft Virtual PC 2007 booting into Ubuntu works just fine!!
Why is it that it works on a Virtual Machine and not on the actual Boot Up?

---

### Post by pmlxuser on 2008-06-12
please go into bios and change an option which talks about hard disk setting
possibly it says SATA just change it to say IDE . Can not explain what happens but when my installtion failed changing this bios feature worked miracles of course the draw back is you have to do the installation again.

Caution!!!: I did this on a machine with one with Ubuntu only, I don't know if micro$oft Window$ will respond right on that. so this should be exercised with caution...

---

### Post by [vu] on 2008-06-12
Maybe.. this question may go to "wubi" forum.
There you can find better answers.. i guess


Cheers

---

