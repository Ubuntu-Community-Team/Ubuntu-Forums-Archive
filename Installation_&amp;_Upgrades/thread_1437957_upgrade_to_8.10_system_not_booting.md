---
title: "upgrade to 8.10 :system not booting"
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by alexcpn on 2010-03-24
Hi, I have been using ubuntu for some years now on on intel pentium 3 550 mhz m/c; Yestreday I uprgaded via upgrade manager to 8.10. The system restarted but it is not booting up. GRUB is the boot manager; I am getting this error;
Kernel panic – not syncing: VFS: Unable to mount root fs on  unknown-block(0 0)
 There is only one disk ; m/c has a cd drive too;
Other than change the bios setting I am unable to do absolutely anything now; 
I guess my only option is to 

1.use some repair cd ? Is there such a thing for ubuntu;

2.Also I can take the hard drive out and connect it to my laptop using an iDE coverter; I can also boot into it using virtualbox.

3.Also I have installed a driver so that I can view the file system in my pc;

I do not want to take out my hard disk; so steps 2 and 3 I do not want to do if possible.

Could some body give me guideance  .Thanks


(Incidently GRUB says press ESC to go to menu; but escape is not goign anywhere; nor c- console or e edit)

---

### Post by tom4everitt on 2010-03-24
Try restoring grub from an ubuntu live cd. 
[http://odzangba.wordpress.com/2007/03/10/how-to-restore-grub-using-the-ubuntu-live-cd/](http://odzangba.wordpress.com/2007/03/10/how-to-restore-grub-using-the-ubuntu-live-cd/)

Make sure you use a pre-karmic version of ubuntu, from karmic and on a different version of grub is used.

---

