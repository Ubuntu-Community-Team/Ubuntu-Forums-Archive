---
title: "How to uninstall a package?"
date: 2005-08-05
forum: Installation &amp; Upgrades
---

### Post by djRob on 2005-08-05
Hi

I have just switched to Ubuntu 5.04 from Windows XP. I updated Ubuntu with linux-image-2.6.10-5-386 ver. 2.6.10-34.3 package, after which sound got worse - when I play real audio or ogg streams one can hear various sound distortions. Can I uninstall this package?
Is there sth like WindowsXP System Restore in Linux?

Thanks in advance,
djRob

---

### Post by jasmuz on 2005-08-05
There isnt a System Restore like Windblows uses (wich sucks by the way)

Do the following:

1-Place your disk in the cdrom drive

2-After its automounted, open a terminal

3-Type cd /media/cdrom/pool/main/l/linux-meta

4-Now type sudo dpkg -i linux-image-386_2.6.10-7_i386.deb

That will install the previous kernel, allowing you to boot with it and remove the one that isnt working properly.

---

### Post by djRob on 2005-08-06
Thanks for the answer.

Can you tell me how can I see wich kernel version I am using, I mean precise version number - during startup system says that I have kernel 2.6.10-5-386 but I don't know how it differs from linux-image-2.6.10-5-386 ver. 2.6.10-34.3 that my system wants to update to?

---

