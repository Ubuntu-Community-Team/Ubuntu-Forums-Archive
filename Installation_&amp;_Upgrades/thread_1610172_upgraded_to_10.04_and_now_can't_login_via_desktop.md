---
title: "upgraded to 10.04 and now can't login via desktop"
date: 2010-10-31
forum: Installation &amp; Upgrades
---

### Post by mluria on 2010-10-31
My 9.10 desktop crashed during installation.  I got to the point where it wanted to remove obselete packages and the keyboard was nonresponsive so I rebooted.  It comes up 10.04, but when I login, the screen goes black for a second and then returns to login screen.  If I type a wrong password, it tells me I have authentication failure.

Pleas help!

m

---

### Post by mluria on 2010-10-31
Noone has any ideas?

I really don't feel, like doing this from the cd.

If I have to, is there an easy way to save my data.  I can boot up as command line.

At this point it won't recognize a usb.

m

---

### Post by mluria on 2010-11-01
tried reinstalling from a cd.  Unfortunately, though it reads the cd, and comes up 10.10  I end up with a 

mount: mounting /dev/loop0 on //filesystem.squashfs failed: ...
Can no mount /dev/loop0 

Evidently this is a fairly common error, and there's not much to do about it other than replace the cd.

I still a command line prompt, and can get out to the internet. Is there a way I can reinstall locally?

m

---

### Post by efflandt on 2010-11-01
What video card/chip do you have, and did you install some video driver other than through System > Administration > Hardware Drivers (or Hardware Drivers originally coming up automatically).  If you installed other video drivers direct from manufacturer, Ubuntu may not be aware how to handle that (even for kernel updates in same distribution version).

But if you cannot get install CD to boot cleanly, you cannot even tell if default video drivers work.  10.04 started using kernel mode setting (kms) by default for some cards, instead of user space video modules.  So in some cases you might need to use **nomodeset** kernel boot parameter.  But I don't think that would explain failure to loop mount squashfs from the CD which is a compressed file system of things needed for the install iso to initiate Linux.

---

### Post by mluria on 2010-11-01
don't really know, don't think I installed anything special.

Is there a way to set the nomodeset kernel boot parameter?

m

---

