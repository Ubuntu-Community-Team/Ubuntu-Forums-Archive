---
title: "Which method of updating to ubuntu 16.04 is quicker"
date: 2016-12-08
forum: Installation &amp; Upgrades
---

### Post by garvind25 on 2016-12-08
Hi there,

I just wanted to know which method of updating to ubuntu 16.04 is quicker:

1. To update the exiting 15.10 version install to 16.04 OR

2. To download 16.04 and make a fresh install?

Thanks,
Arvind Gupta.

---

### Post by #&amp;thj^% on 2016-12-08
You may get different answers here from different users...but in my HMO opinion down-load the 16.04 iso..and  have a clean install.
It seems to make a nicer user experience that way.
Just my 2 cents worth.
Kind Regards

---

### Post by deadflowr on 2016-12-08
In a perfect, no problems occur world, an upgrade is quicker than an install.
That's if you want wholesale upgrade of all your existing packages and settings.

As an upgrade upgrades everything to the latest package in one fell swoop.

Where as a fresh install requires downloading + getting it on some media + installing + updating + installing software not included on the installation that you want, again.
(and that's not even counting the time to restore your backups, and setting up any secondary user accounts, and having to reset any setting configuration that requires new action not set in any restored backup configuration file...)


That said, the world is not perfect.

And upgrading from a dead release increases those imperfections.

So while an upgrade can be quicker, the above recommends of a fresh install, in particular for this upgrade, is preferred.

---

### Post by ian-weisser on 2016-12-08
Depends upon your download bandwidth.
Depends upon how quickly your data backups/restoration take.
Depends upon how much (if any) non-Ubuntu software and other customizations you must uninstall/reinstall.

I think the OP has oversimplified the question.
I have several systems that take about two hours to uninstall non-Ubuntu software, release-upgrade, deconflict the customized config files, and reinstall the non-Ubuntu software.
I also have several systems that take about two hours to backup data, fresh-install, customize, and install the non-Ubuntu software.
...but I know exactly what I want to do for both cases.

---

### Post by garvind25 on 2016-12-09
Well I downloaded the iso and did a fresh install on my system (already having win 7). I made sure I did not select the option for wiping the HDD during the installation. On rebooting, GRUB is only showing ubuntu installation and not both!!! What do I do now?

Arvind Gupta

---

### Post by oldfred on 2016-12-09
Run this:
sudo update-grub

If not, post this:
sudo parted -l

Did you create new / (root) partition with gparted and install to that. 
Or use Something Else and overwrite old install and restore your data from backups?

---

