---
title: "[SOLVED] Upgrade to 8.04.1 locales 2.7.9-4 is broken"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by Edifier1007 on 2008-08-23
Hi,

I tried the upgrade to 8.04.1 from 7.10 today and now my installation is broken.

It took quite a bit to download and install but got stuck when about 20 mnts of installation time was remaining. The last set of messages were for generation of locales. 

I had to reboot. Post reboot, my initial login prompt screen comes up but normal boot is not successful. It kind of hangs before painting the desktop. After a few trial and errors, I went thru Failsafe option. The network is not connected any longer.

Any attempt to run any upgrade related programs (dpkg, dselect, aptitude) result finally in 'run dpkg --configure -a' message. 

That gets stuck at the same stage of installing locales 2.7.9-4 package. dpkg audit states that it is partially installed. I can not remove it nor it finishes intallation now !!

Can anyone help ?

Thanks in advance.

---

### Post by cariboo on 2008-08-23
You could try this in a terminal:

```
sudo dpkg --remove --force-remove-reinstreq locales 2.7.9-4
```

Jim

---

### Post by Edifier1007 on 2008-08-24
Hi Jim.

Thanks for the suggestion. I tried it and it removed locales for me but problem did not get resolved.

I tried some more search and found that this is a bug. Actually there is more than one thread open on this. Here is one reference that helped me.

[http://www.archivum.info/ubuntu-bugs@lists.ubuntu.com/2008-07/msg38393.html](http://www.archivum.info/ubuntu-bugs@lists.ubuntu.com/2008-07/msg38393.html)

My installation is working now but as a result of all this, only in English locale currently. 

Seems like kernal version XXX-15 is buggy. The current one seems to be xx-19.

Thanks for the help.

---

### Post by Edifier1007 on 2008-08-24
All: 

Here is more comprehensive discussion on this. 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/249340](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/249340)

---

