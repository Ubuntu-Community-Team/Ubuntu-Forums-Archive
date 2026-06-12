---
title: "Installing ATI proprietary drivers on Lubuntu 13.10"
date: 2013-10-31
forum: Installation &amp; Upgrades
---

### Post by Elastic_Potential on 2013-10-31
Hey all,

After performing a clean install of Lubuntu saucy, I followed [this guide]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") to install ATI drivers from the AMD website.  When I reached the point of installation, I was greeted with this error:

```

nergal@Aeon:~/Downloads$ sudo dpkg -i fglrx*.deb 
[sudo] password for nergal: 
(Reading database ... 118574 files and directories currently installed.)
Preparing to replace fglrx 2:12.104-0ubuntu1 (using fglrx_12.104-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx ...
Preparing to replace fglrx-amdcccle 2:12.104-0ubuntu1 (using fglrx-amdcccle_12.104-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx-amdcccle ...
Preparing to replace fglrx-dev 2:12.104-0ubuntu1 (using fglrx-dev_12.104-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx-dev ...
dpkg: dependency problems prevent configuration of fglrx:
 fglrx depends on dkms; however:
  Package dkms is not installed.

dpkg: error processing fglrx (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.

dpkg: error processing fglrx-amdcccle (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-dev:
 fglrx-dev depends on fglrx; however:
  Package fglrx is not configured yet.

dpkg: error processing fglrx-dev (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
 fglrx-dev
nergal@Aeon:~/Downloads$ 

```

Granted, Saucy was just released and is bound to have it's share of bugs, but I've followed this guide many times before, and this is the first time I've ran into an error like this.

Anyone have any ideas?

Thanks

---

### Post by Dennis N on 2013-10-31
It it were me, to begin with I would install **dkms** and try again. 

**sudo apt-get install dkms**

---

### Post by Elastic_Potential on 2013-10-31
Incidentally, I realized that error immediately after posting this topic.  After doing so, I guess it installed, but not properly.  Upon running aticonfig --initial, rebooting, and logging in, my desktop never loaded; instead, I was greeted to a black screen, a frozen mouse, and an inactive desktop.  After fifteen/twenty seconds, I am logged-out and returned to LightDM.

What even.

---

### Post by Elastic_Potential on 2013-11-01
Okay, I was able to remove those drivers and log back in to my system.  Following that same guide, I was able to install the fglrx and fglrx-amdcccle drivers from the repos, performed a reboot, and logged back in.  Lubuntu 13.10 isn't playing nicely with these drivers either.  The most noticeable errors were: the screen brightness adjust is out of whack; it won't suspend sometimes; when it does suspend, the wireless card won't work after waking it up.

I guess I'll leave this open, and if anything changes in the future, hopefully someone will reply.  It's important to me that I get these drivers to work because I'm on a netbook with a C-50 APU; without them, the heat output is significant.  In any case, I might just revert to 13.04 or give another distro a try.

Help with this issue would still be appreciated.

---

