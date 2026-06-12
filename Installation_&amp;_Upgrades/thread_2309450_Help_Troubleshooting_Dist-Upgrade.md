---
title: "Help Troubleshooting Dist-Upgrade"
date: 2016-01-10
forum: Installation &amp; Upgrades
---

### Post by mlnease on 2016-01-10
Hello,

I've just upgraded from Trusty to Vivid.  I did this by editing ```
/etc/apt/sources.list
``` replacing 'trusty' with 'vivid'; then running 
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```I've since gathered I would've been wiser to use Update Manager--live and learn.

The update and upgrade were very rocky but after jumping through a lot of hoops I finished, recovered my network connections and finished the upgrade.

Now, however, when I boot I receive 10 or eleven of the attached error messages.  Also, when I reload Synaptic I receive these 'Failed to fetch' messages:

   Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/vivid/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/vivid/main/source/Sources)  404  Not Found [IP: 91.189.92.152 80]
 Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/vivid/main/binary-amd64/Packages](http://extras.ubuntu.com/ubuntu/dists/vivid/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.152 80]
 Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/vivid/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/vivid/main/binary-i386/Packages)  404  Not Found [IP: 91.189.92.152 80]
 Some index files failed to download. They have been ignored, or old ones used instead.

Any advice would be much appreciated--thanks in advance.

---

### Post by grahammechanical on 2016-01-10
An interesting experiment.

Ubuntu 15.04 is about to reach end of life in about 4 weeks. You would have been better waiting another 4 months and then upgrading to 16.04. Now, you need to think about moving on to 15.10 and then 16.04 sometime in the summer.

In my opinion the failed to fetch errors are not so important as the "system problem detected" messages. But it may be possible to live with them if the system is still usable. Updating may fix a few things but a lot depends upon what is triggering the message. To find that out you need to click "report the problem." That should produce some detail & you can still decline to actually report the problem.

Upgrading to 15.10 will not necessarily fix these problems. So, start thinking about doing a fresh install of 16.04. That is my advice.

Regards

---

### Post by mlnease on 2016-01-10
> **grahammechanical said:**
> An interesting experiment.

Ubuntu 15.04 is about to reach end of life in about 4 weeks. You would have been better waiting another 4 months and then upgrading to 16.04. Now, you need to think about moving on to 15.10 and then 16.04 sometime in the summer.

In my opinion the failed to fetch errors are not so important as the "system problem detected" messages. But it may be possible to live with them if the system is still usable. Updating may fix a few things but a lot depends upon what is triggering the message. To find that out you need to click "report the problem." That should produce some detail & you can still decline to actually report the problem.

Upgrading to 15.10 will not necessarily fix these problems. So, start thinking about doing a fresh install of 16.04. That is my advice.

Regards

Thanks for your the speedy response.  I did 'report the problem' a few times but found Sourceforge's instructions a bit over my head (I'm not a programmer).

I was in no rush to upgrade (I always prefer LTS's) but discovered that my DVD backups (from AVIs using Devede) were failing (no audio) due to the absence of ffmpeg in the Trusty repos.  I didn't (and don't) want to wait four months to remedy this.

I guess my only realistic option is to reinstall 14.04 and forget about backing up DVDs for the forseeable future.  At least I'll have an unbroken OS in the meantime.

Thanks again for your time and attention.

New developments:  When I logged on this AM, the 'Failed to fetch' and error messages problems had resolved themselves.  So for a minute my problems were solved.  However, I was presented by Update Manager with the opportunity to upgrade again to a new version of 15.04 (I forget the decimal), which I did.  All went swimmingly.  But this time, when I rebooted, there was about a one minute latency before the log-on screen appeared; and when I selected my username and entered my password, the screen went black.  Same results for two new reboots.

So I'm working from a Trusty live CD and have access to the Vivid partition--all the data looks normal.  I've installed gksu and nautilus, but ```
gksudo nautilus
``` returns nothing.

I also tried ```
sudo update-grub
``` which returned ```
/usr/sbin/grub-probe: error: failed to get canonical path of `/cow'
```.

Any advice would be greatly appreciated--thanks again in advance.

---

### Post by mlnease on 2016-01-11
EDIT

Since my original problems with this upgrade are resolved, I'll mark this thread solved.  New problems have ensued and I'll start a different thread for them.

---

