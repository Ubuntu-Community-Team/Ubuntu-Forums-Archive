---
title: "adjusting  ubuntu iso to give a different default 'guided' install"
date: 2013-08-09
forum: Installation &amp; Upgrades
---

### Post by linuxonbute on 2013-08-09
Hi all,
I wonder if it's possible to download a standard ubuntu iso and edit it so that when selecting the guided install
it will create /, swap and /home with either a fixed / of say 50GB, maybe 2GB swap and the rest for /home
Or for that matter something else?
Any ideas please?

---

### Post by oldfred on 2013-08-09
It is difficult to automate all the extra partitions. It depends on what partitions you have, what space is available and what space you want for each partition.

Best just to use Something Else or manual install and create partitions of the size you want. I do prefer to create partitions in advance with gparted, but still have to use manual install to choose which partition is / (root) which is /home and which is swap. Also formats and whether to reformat which you would not want to reformat an existing /home. 

I typically install in 25GB / , but have all data in other data partitions. Then my /home is still in / but very small so easy to backup.

Install screens and process are nearly identical for all recent versions.
       Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 

 Install with screen shots:
[http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT](http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT)
Install options, Do not use erase entire drive unless that is really what you want. That is entire hard drive not just Windows c: "drive".
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://askubuntu.com/questions/6328/how-do-i-install-ubuntu](http://askubuntu.com/questions/6328/how-do-i-install-ubuntu)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)

---

### Post by linuxonbute on 2013-08-09
thanks for the info. problem is I live in Scotland and I would like to set up an iso for install on a specific laptop.
Reason for me wanting to do it this way is that the person using it is not good at installation and needs a large /home
on it's own partition. It would be easy to just go and do it manually except laptop is in Vancouver area!

---

### Post by ian-weisser on 2013-08-09
Perhaps a phone call while they try to install might be a more convenient solution for everyone...for a single install.

---

