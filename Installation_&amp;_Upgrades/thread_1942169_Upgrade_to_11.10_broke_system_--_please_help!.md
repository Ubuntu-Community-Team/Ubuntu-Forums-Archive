---
title: "Upgrade to 11.10 broke system -- please help!"
date: 2012-03-17
forum: Installation &amp; Upgrades
---

### Post by vinoloco on 2012-03-17
Hi All,

I just upgraded my perfectly functioning Ubuntu install to 11.10 and now have issues...

I can log in but all I see on the monitor is the splash screen!  There are no icons or menu bars so I can't proceed from there.

I can easily log in so I'm guessing this is and easily fixed problem.  Can anyone help me out?

Thanks in advance...

  vino

---

### Post by raja.genupula on 2012-03-17
you have to reinstall your graphics drivers again . what kind of desktop drivers you have ?

to get into desktop ....

choose Grub recovery mode and failsafeX mode from that .

---

### Post by vinoloco on 2012-03-17
Thanks for the help here Raja.

How do I go about booting into failsafeX mode?  I can boot through GRUB to the regular failsafe mode but this only gets me to a text prompt.

Also, I have no idea what my desktop drivers are.  I guess just the ones which installed when I updated to 11.10?   I have to admit I'm a novice when it gets to details like that.  I'm just bummed that my system was working fine and now I can't do anything with it...  :-(

Let me know if you have any other ideas.

  vino

---

### Post by darkod on 2012-03-17
There is a sticky on top of the threads for video issues. It has a detailed explanation what to do.

---

### Post by vinoloco on 2012-03-17
OK, read the sticky and all I had to do was type:  sudo services gdm start and that worked

-- vino

---

