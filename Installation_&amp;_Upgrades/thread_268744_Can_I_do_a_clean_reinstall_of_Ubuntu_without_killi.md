---
title: "Can I do a clean reinstall of Ubuntu without killing Grub?"
date: 2006-09-30
forum: Installation &amp; Upgrades
---

### Post by edgydominator on 2006-09-30
Just wondering, since an attempted upgrade to Edgy Eft from Dapper resulted in x failing to start. I've tried multiple ways to fix this, but to no avail. So, I want to do a clean install, but I am running grub and also have Win XP on the machine. So, if I clean install, will I still be able to boot?

Thanks.

---

### Post by Herman on 2006-09-30
Did you try to fix you old Xserver by running 'sudo dpkg-reconfigure xserver-xorg'.........................................................................[Xserver Page]("http://users.bigpond.net.au/hermanzone/p7.html") ?


Download for yourself a copy of the latest  [Super Grub DIsk]("http://adrian15.raulete.net/grub/tiki-index.php")  and burn it to a CD, you'll be able to do just about anything.
You can also get Super Grub Disk for USB and floppy disks as well, just look around on that site.

You should not need it though, as Ubuntu's installer will scan your computer and automatically add all other operating systems to your new Grub's menu automatically for you in most cases. It will also automatically install your new Grub to MBR for you, so you won't need to worry about a thing. 
There is a tiny percentage of installations where Grub needs a iittle help to be configured properly, mainly when there are more than one hard disk and when IDE and SCSI (sata) disks are combined. Some Sata disks give Grub problems on their own. Normally the problems are easy to solve by editiing /boot/grub/menu.lst
Grub Page................................................................................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm")

Regards, Herman :D

---

### Post by orb9220 on 2006-09-30
During a clean install it will see the xp partition and write the new grub with xp as an option in grub is that what you mean?

---

### Post by lha on 2006-10-01
I believe Ubuntu installer detects Windows only if mbr contains Microsoft's boot code. If you reinstall Ubuntu, Windows may disappear from Grub. Don't worry, though. It's easy to add fix this. There are many threads in the forums on this subject. Find one of them or look at your own /boot/grub/menu.lst.

---

### Post by orb9220 on 2006-10-01
[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

---

