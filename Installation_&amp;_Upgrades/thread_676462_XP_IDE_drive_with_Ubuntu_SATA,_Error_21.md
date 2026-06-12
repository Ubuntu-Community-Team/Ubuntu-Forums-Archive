---
title: "XP IDE drive with Ubuntu SATA, Error 21"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by hanktacoma on 2008-01-23
Lo!,

I'm trying to install Ubuntu 7.1 on a second hard drive, a SATA, while XP lives on the first hard drive, an IDE.  After installing Ubuntu, and during its first reboot, I got a message like this on the way down. 

"Grub loading...  Stage 1.5...  Please wait... Error 21."

I hesitate to reload Ubuntu again until I know what happened and why. I have a copy of (Keir Thomas) "Beginning Ubuntu Linux" It doesn't cover 7.1 Gutsy.  I can't get the fix on page 80 to work from the distro:

(tried zeros and upper/lower case o)

sudo grub
root (hd0,1)
setup (hd0)
quit

Thanks in advance,
hanktacoma

---

### Post by Pumalite on 2008-01-23
[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)

---

### Post by push_harder on 2008-01-23
Download Super GRUB.
[www.supergrub.forjamari.linex.org](www.supergrub.forjamari.linex.org)

You can use a CD or USB stick (if you're BIOS can boot from USB)
And this will allow you to boot either linux or ubuntu.

BUT!, when you're booted back into linux, let me know an d i'll let you know what to do from there.


Cheers, Matt

---

### Post by logos34 on 2008-01-23
> **hanktacoma said:**
> 
sudo grub
root (hd0,1)
setup (hd0)
quit


Sounds like grub overwrote the windows bootloader on the ide drive MBR.


I think you want (hd1,1).  (i.e. second drive, second partition).

Reboot and press 'e' to edit the ubuntu kernel, then 'e' again on 'root' line...change to (hd1,1) or (hd1,0) if it's on the first partition.  Then 'enter' and 'b' to boot.  If it works make the change permanent:

gksudo gedit /boot/grub/menu.lst

---

### Post by hanktacoma on 2008-01-24
> **hanktacoma said:**
> Lo!,

I'm trying to install Ubuntu 7.1 on a second hard drive, a SATA, while XP lives on the first hard drive, an IDE.  After installing Ubuntu, and during its first reboot, I got a message like this on the way down. 

"Grub loading...  Stage 1.5...  Please wait... Error 21."

I hesitate to reload Ubuntu again until I know what happened and why. I have a copy of (Keir Thomas) "Beginning Ubuntu Linux" It doesn't cover 7.1 Gutsy.  I can't get the fix on page 80 to work from the distro:

(tried zeros and upper/lower case o)

sudo grub
root (hd0,1)
setup (hd0)
quit

Thanks in advance,
hanktacoma
Thanks to pumalite and push-harder.  I'll try one of the answers when time permits.  It's late at night here but for now I just want to let you know I appreciate the help.

---

### Post by hanktacoma on 2008-01-28
The problem is solved, I'm using Ubuntu now!  Thanks again to the three responders.  :)

---

### Post by Pumalite on 2008-01-28
Glad you got it solved.

---

### Post by hanktacoma on 2008-05-20
I'm not quite far enough along yet to chance rewriting grub but I have four books and another on the way.  In the meantime I have two computers and plenty of time to experiment without losing my connection to the community for very ling at a time.  I hope to digest the books soon enough to return the help.

Thanks again to all.

---

