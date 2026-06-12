---
title: "no xsession - I messed up my graphics set up - Help !"
date: 2005-07-03
forum: Installation &amp; Upgrades
---

### Post by ricardo06 on 2005-07-03
I did some stange installation after i read some advices on how to improve 3D with my ati chipset. 
The result is that I can no more start an xsession.  I still have the rescue session.
the xsession error log says it cannot find 'libatk-bridge' module.
How can i go back to the standard ubuntu graphics installation without re-installing from scratch and loosing a month work ?

I am running hoary 5.04 on amd64 with kernel 2.6.11

Thanks A LOT to anaybody that can help.

Richard

---

### Post by sethmahoney on 2005-07-03
If you reinstall, you shouldn't lose any data from your prior installation if your /home is on its own partition.  You'll only lose any additional programs you installed.

Probably your best bet for getting your X working again without reinstalling is to figure out the changes you made and undo them in the rescue session.

---

### Post by mtron on 2005-07-03
did you try "sudo dpkg-reconfigure xserver-xorg"  and choosing another driver, like vesa ?

---

