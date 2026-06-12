---
title: "dual boot question"
date: 2007-07-01
forum: Installation &amp; Upgrades
---

### Post by vbdanl on 2007-07-01
I have read lots of posts about dual booting, most deal with one hard drive. I have a hd with windows 98 on it.  Another hard drive with ubuntu on it.  Ubuntu was loaded without the 98 drive attached.  Is it possible to install the 98 drive as the secondary drive by changing the pins, and modify the menu.lst file on the ubuntu drive to give the option of booting either drive?  thanks in advance for your help.

---

### Post by confused57 on 2007-07-02
> **vbdanl said:**
> I have read lots of posts about dual booting, most deal with one hard drive. I have a hd with windows 98 on it.  Another hard drive with ubuntu on it.  Ubuntu was loaded without the 98 drive attached.  Is it possible to install the 98 drive as the secondary drive by changing the pins, and modify the menu.lst file on the ubuntu drive to give the option of booting either drive?  thanks in advance for your help.
Yes, it's quite easy to set up:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by vbdanl on 2007-07-03
thanks.  i added the lines to the menu.lst as suggested, and it worked fine.
both ubuntu and windows boot up.
now i just need to figure out if i can trim ubuntu 6.06 down enough to live on the 2.5 GB hd.  It is 88% full, so not sure how long that will work.  may need to try xubuntu or something else smaller.
any suggestions?

---

### Post by confused57 on 2007-07-03
> **vbdanl said:**
> thanks.  i added the lines to the menu.lst as suggested, and it worked fine.
both ubuntu and windows boot up.
now i just need to figure out if i can trim ubuntu 6.06 down enough to live on the 2.5 GB hd.  It is 88% full, so not sure how long that will work.  may need to try xubuntu or something else smaller.
any suggestions?
This will help some:
[http://doc.gwos.org/index.php/RemoveJunkFiles](http://doc.gwos.org/index.php/RemoveJunkFiles)

Xubuntu probably won't be that much lighter, especially for a 2.5 Gb hd...you might consider Puppy Linux:
[http://www.puppylinux.com/download/downpage.htm](http://www.puppylinux.com/download/downpage.htm)
I have Puppy-215CE installed on a 2.0 Gb partition...the desktop is impressive, you might want to at least try out the live cd if you're interested.

---

