---
title: "Error after installing Ubuntu Netbook Remix, totally stumped"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by trav3ler on 2009-12-26
Hey, so I got a new Netbook today, decided to try and install Ubuntu on it.  Figure I'm never gonna need Windows again, so I install Ubuntu over windows, and it works great for about 3 hours.  Then, I go to boot up the netbook again, and get this:

mounting dev/disk/(snip) on /root failed: Invalid argument
mounting /sys on /root/sys failed: No such file or directory
(same as above for /dev, /sys, and /proc)
Target filesystem doesn't have /sbin/init
No init found.  Try passing init= bootarg.

So I try dicking around in the command line for a while, but I pretty much don't know what I'm doing (fairly new to Linux), so I'm not able to fix it.  I figure, no big deal, I'll go get the boot disk USB i made and reinstall off of that.  Go to plug it in, and the computer won't recognize the USB or boot off of it.  I tried BIOS, everything I could think of, but it keeps trying to book the corrupted install of Ubuntu and throwing this error at me.

Any ideas?  As of right now I have a brand new bricked netbook, and I'm a little upset about it...  can someone help a poor linux newb?

---

### Post by Vermind on 2009-12-26
You can change the boot priority from BIOS setup (F2 or Esc or Del during boot). In case your BIOS does not let you do this, start the computer with the usb mem stick in, and try pressing F11 or Esc for the boot options, and try to boot the usb mem stick.

As for what is wrong with your install, I have no idea. I can only guess that it is trying to boot something else than the primary hard drive, or your primary hard drive did not get GRUB during install and has an old one. Also, if you press shift or esc during boot of GRUB, and you see multiple kernels in the list, you could try an older one, or the recovery mode of the current one. If you get into your system, check how big your /boot is (out of space means some kernels might not be completely installed), and try ```
sudo update-grub
``` and ```
sudo grub-install /dev/sda
``` to get grub on your main hd.

---

### Post by trav3ler on 2009-12-26
Aha, thanks for the help!  Was able to find the boot drive, am now able to reinstall!  Hopefully I won't do whatever I did last time that screwed it up :)

---

