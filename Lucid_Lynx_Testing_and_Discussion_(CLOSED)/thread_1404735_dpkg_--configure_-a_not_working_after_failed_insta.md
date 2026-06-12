---
title: "dpkg --configure -a not working after failed install"
date: 2010-02-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by deathsshadow77 on 2010-02-11
so long story short my install got interrupted on my lucid install and now I cant use sudo dpkg --configure -a since I get this error message from initramfs
"cpio: ./lib/udev/firmware.sh: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.32-12-generic
dpkg: subprocess installed post-installation script returned error exit status 1"
Ive tried just running an update to see what would happen but still nothing

---

### Post by cariboo on 2010-02-11
Copy and paste the commands from [this]("http://ohioloco.ubuntuforums.org/showpost.php?p=8804847&postcount=22") post in a terminal, then run sudo dpkg --configure -a, it worked for me.

---

### Post by emarkay on 2010-02-12
I fixed it with this method: 
[I]
edit /usr/sbin/update-initramfs and add a "exit 0" directly after set -e
[/I]
[http://ohioloco.ubuntuforums.org/showthread.php?p=8804847#post8804847](http://ohioloco.ubuntuforums.org/showthread.php?p=8804847#post8804847)

---

### Post by VMC on 2010-02-12
> **emarkay said:**
> I fixed it with this method: 
[I]
edit /usr/sbin/update-initramfs and add a "exit 0" directly after set -e
[/I]
[http://ohioloco.ubuntuforums.org/showthread.php?p=8804847#post8804847](http://ohioloco.ubuntuforums.org/showthread.php?p=8804847#post8804847)

That doesn't fix it, that stops "update-initramfs" from working.

cariboo907's link is preferred, or even this [link]("http://ohioloco.ubuntuforums.org/showpost.php?p=8804856&postcount=25").

---

### Post by emarkay on 2010-02-12
> **VMC said:**
> That doesn't fix it, that stops "update-initramfs" from working.
cariboo907's link is preferred, or even this [link]("http://ohioloco.ubuntuforums.org/showpost.php?p=8804856&postcount=25").

Yes, in testing another PC, I agree - you are correct.

If one did the above, don't forget to remove *"exit 0"* afterward.

---

### Post by deathsshadow77 on 2010-02-12
thanks. I ended up deleting all the files in /var/lib/dpkg/updates and that seemed to work. should i still run those commands anyway? everything seems fine.

---

### Post by VMC on 2010-02-12
> **deathsshadow77 said:**
> thanks. I ended up deleting all the files in /var/lib/dpkg/updates and that seemed to work. should i still run those commands anyway? everything seems fine.

That all depends. If you used the "exit 0", then "update-initramfs -u" never works. You just get a new line after issuing the command.

It should say something like this:
"update-initramfs: Generating /boot/initrd.img-2.6.32-13-generic"

---

### Post by cookiecruncher on 2010-02-12
```
**dpkg --configure -a**
``` worked for me.

---

