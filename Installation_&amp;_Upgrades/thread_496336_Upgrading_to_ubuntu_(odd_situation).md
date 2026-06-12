---
title: "Upgrading to ubuntu (odd situation)"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by kidl33t on 2007-07-09
Howdy all,

I am just working on trying to upgrade my laptop to ubuntu.  I currently have an old version of slackware installed.  There are some issues however.   The laptop doesn't have a CD drive.  It also has no floppy drive and is incapable of booting from USB.  I installed slackware by putting the harddrive from this laptop into a friends laptop, booting from the old slackware CD I borrowed from another friend,  and then after it copied its files over and rebooted I (sneakily!) yanked the hard drive out and threw it back into my POS laptop before it configured itself.  It actually worked very well.  I have lots of experience with computers but am fairly new to linux.

For my college program however we are required to use ubuntu so I was hoping to upgrade to it.  Does anyone know of a method to do this?  I have downloaded an ubuntu ISO and mounted it, but i can't get it to run at all.  Also, due to the first slackware installation my boot loader is lilo not grub.  I don't know if that is an issue.  

Any responses would be quite helpful.  Thanks!

PS if I pull the network cable out of my  laptop, I have to reboot to get my network connection back.  I used to be able to do something like 'ip link set eth0 up' or something to make it work.    That doesnt do the trick now though.  Anyone know?  The rebooting is just annoying hehe.

---

### Post by renzokuken on 2007-07-09
you could try a "network install" there are guides in the wiki and help pages.

as for the network command, in ubuntu its

```
sudo ifdown eth0
``` to drop the connection

and

```
sudo ifup eth0
``` to restart the connection

not sure how relevant they are to slackware though, obviously the "sudo" part is obsolete

---

### Post by kidl33t on 2007-07-09
Thanks Renzokuken.  It's good advice.  

Does anyone know a good network install guide?  All the ones I've been able to find require booting from a live CD which I cannot do.  

Otherwise a decent guide on how to boot from an ISO I've already downloaded would probably work.  If anyone has an ideas I would really appreciate it.  

Thanks

---

### Post by renzokuken on 2007-07-10
here is one guide i found

[http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)

both [www.ubuntugeek.com](www.ubuntugeek.com) and [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) are excellent sites for guides , tutorials and tips

---

