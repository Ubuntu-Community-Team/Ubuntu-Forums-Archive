---
title: "Upgrading from 7.10 to 8.04.1"
date: 2008-07-22
forum: Installation &amp; Upgrades
---

### Post by MrWES on 2008-07-22
OK.. I finally feel comfortable in upgrading to Hardy 8.04. My box is set up with / and /home on separate partitions, and I plan on doing a fresh install. Will I have to reinstall packages I currently have installed that do not install on default? Or will they still run ok? What other post "fresh" install maintenance will I need to do?

Thanks,
Bill

---

### Post by Pumalite on 2008-07-22
You can save some in a CD or DVD with APtonCD:
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)
The rest you will have to reinstall.
You can also go to Synaptic>File>Generate Package Download Script.

---

### Post by audwan on 2008-07-22
Yes, you need to reinstall packages if you reinstall over your current installation. If you want to keep your packages, you might want to try an upgrade. It's not that much work to install packages though. I use the same method, and it doesn't take me many minutes.

I don't do anything beyond installing packages, but it really depends on your setup. All I can think of is changes you've done to xorg. A backup of /etc/xorg.conf and other configuration files you have changed that doesn't reside on /home is a smart move anyway.

Just make sure you don't format /home when you reinstall, thats all ;)

---

### Post by MrWES on 2008-07-22
Hrmm..Ok -- don't format /home :)

Anyhow, I tried an upgrade on my son's box running 7.10 and it hung as described on this thread:

[http://ubuntuforums.org/showthread.php?t=865679]("http://ubuntuforums.org/showthread.php?t=865679")

I guess it was something with the newest, current kernel. It just baffles me the people running pretty solid boxes with 7.10 and they puke on an upgrade to 8.04.

I think I'll go the fresh install route, with the mediabuntu repository enable after the up grade.

Thanks,
Bill

---

