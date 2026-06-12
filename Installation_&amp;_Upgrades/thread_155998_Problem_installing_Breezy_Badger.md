---
title: "Problem installing Breezy Badger"
date: 2006-04-06
forum: Installation &amp; Upgrades
---

### Post by percyt on 2006-04-06
I have a customer who wants a server to run LTSP and as Ubuntu has it installed by default, that's the flavour of Linux we're going to go with.

The server in question is a Compaq Proliant ML370 - [HERE](http://cgi.ebay.co.uk/Compaq-Proliant-ML370-Dual-PIII-1GHhz-Server_W0QQitemZ5876511050QQcategoryZ1484QQrdZ1QQcmdZViewItem) is a link to it which my customer bought off ebay.

The server only has a CDROM drive so I downloaded the CD ISO to install.

It seemed to go well until it said it was finished and wanted to reboot from the kernel - then I get this on boot up:-

---------------------------------------------------------------------------
Booting 'Ubuntu, kernel 2.6.12-9-386 '

root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83
kernel  /boot/umlinuz-2.6.12-9-386 root=/dev/ida/c0d0p1 ro quiet splash
   [Linuz-bzImage, setup=0x1c00, size=0x124b1b]
initrd  /boot/initrd.img-2.6.12-9-386
   [Linuz-initrd @ 0x1fb3a000, 0x4b565e bytes]
savedefault
boot
Uncompressing Linux... Ok, booting the kernel.
Loading , please wait...
ALERT! /dev/ida/c0d0p1 does not exist. Dropping to a shell!


Busybox v1.00=pre10 (Debian 20040623-1ubuntu22) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
#

-------------------------------------------------------------------------

Not sure what this means (apart from c0d0p1 missing)

Any help greatly appreciated.

Many thanks,

Darren

---

### Post by bjweeks on 2006-04-06
Best bet would be to try reinstalling.

---

### Post by percyt on 2006-04-06
Just done that after running the SmartStart CD and removing everything from the disk.

Still nothing.

Any ideas?

---

### Post by bjweeks on 2006-04-06
The cd might be bad or bad hardware.

---

### Post by percyt on 2006-04-06
I'm thinking it could be hardware - which is a problem as it needs to be this server!

One thing though, it won't boot off an Ubuntu DVD, but the DVD has just installed fine on another basic pc.

---

### Post by bjweeks on 2006-04-06
[QUOTE=percyt]I'm thinking it could be hardware - which is a problem as it needs to be this server!

One thing though, it won't boot off an Ubuntu DVD, but the DVD has just installed fine on another basic pc.[/QUOTE]

Does it have a DVD reader? Also some dvd readers wont boot dvd's.

---

### Post by percyt on 2006-04-06
I've fitted a DVD drive and it won't see the dvd to boot from.
It boots CD's fine.

I'll try another DVD drive to see if it's that drive that won't see the disk.

But what's this about "ALERT! /dev/ida/c0d0p1 does not exist."

---

### Post by bjweeks on 2006-04-06
If you google /dev/ida/c0d0p1 you will see a few pages talking about install linux of a proliant.

[http://www.joelschneider.net/compaq_proliant_1500_debian_potato.html](http://www.joelschneider.net/compaq_proliant_1500_debian_potato.html)
[http://www.cpqlinux.com/pl1500rh62.html](http://www.cpqlinux.com/pl1500rh62.html)

---

### Post by cocox on 2006-05-15
maybe this can help you, good luck

[http://www.ubuntuforums.org/showthread.php?p=1017808#post1017808](http://www.ubuntuforums.org/showthread.php?p=1017808#post1017808)

:mrgreen:

---

### Post by DavidRa on 2006-05-20
Hi Percy

[http://www.ubuntuforums.org/showthread.php?t=82466](http://www.ubuntuforums.org/showthread.php?t=82466) should have the answer to your question - look for vjshah's answer about 3-4 posts from the top. You may not be able to follow the procedure blindly but it should get you to the right place. I got my DL380 installed using a slightly tweaked version of that procedure.

---

