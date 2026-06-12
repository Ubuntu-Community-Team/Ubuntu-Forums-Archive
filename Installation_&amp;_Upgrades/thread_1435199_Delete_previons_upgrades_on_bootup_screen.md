---
title: "Delete previons upgrades on bootup screen"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by taoist53 on 2010-03-21
I have 9.04 installed.  When I boot up i see all the iterations since the 1st install on my boot up screen.  How do I delete these?  I have to scroll to get to my other OS's.

I am running a multiple boot setup.

Thanks for any help in advance.

taoist53:confused:

---

### Post by n0dix on 2010-03-21
Go to /boot/grub/menu.lst file and comment (add # symbol) at the beginning of the line you want ignored. 

If you are not sure, post your menu.lst file.

---

### Post by Enigmapond on 2010-03-21
What you are seeing are probably just previous kernels. You can change this in system/administration/startup manager and go to the advanced tab and change the  number to 2. It's always good to show at least one previous kernel just in case you need to boot up on it.

Another way, to delete them entirely, is install Ubuntu Tweak. This has a function to zap all previous kernels.

---

### Post by taoist53 on 2010-03-28
Thanks for the responses.  I knew there had to be a way.
taoist53

---

