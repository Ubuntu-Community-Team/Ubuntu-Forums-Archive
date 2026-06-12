---
title: "Hung while upgrading @ Running post-installation trigger update-notifier-common"
date: 2013-06-15
forum: Installation &amp; Upgrades
---

### Post by mvsrinivas on 2013-06-15
Hi,

I was installing updates to ubuntu 12.04 on my laptop. It was installing slowly and left it overnight to install. In the morning, I found that the update install process has hung. Can somone please help or suggest what could be wrong. Looks like I cannot stop the process either. Here is the screenshot:

Cheers,
Srini

---

### Post by 2F4U on 2013-06-15
Seems as if it got stuck while downloading. Did the machine go to sleep or got it disconnected from the network (happens more likely when connected wireless)?

---

### Post by mvsrinivas on 2013-06-16
> **2F4U said:**
> Seems as if it got stuck while downloading. Did the machine go to sleep or got it disconnected from the network (happens more likely when connected wireless)?

Yes, it was connected over wireless. Machine neither went to sleep nor got disconnected. I had to forcefully shut down by pressing the power button of laptop and boot again. It updated properly afterwards.

Thanks!

---

### Post by Rafael_Junqueira_Santos on 2013-10-02
Hi, I have the same problem, but with other reason:
My installation hung all the times because of this, so I cancelled it and tried to repair it with the live CD:

boot-repair gave me this solution:
> dpkg-error detected. Please open a terminal then type (or copy-paste) the following command:

sudo chroot "/mnt/boot-sav/sda2" dpkg --configure -a

So I did it, and it stopped in this part:
> Setting up update-notifier-common (0.145) ...
flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.310.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.310.orig.tar.gz)
So I checked the link and tried to download manually to see if it was working. In fact, it is, but downloading at a 6KBps rate, meaning I would have to wait 40 min to download the 13MB file.
So the installation didn't actually freeze for me, it was just taking too much time because of this slow link, without giving feedback.

Edit: I'm using Ubuntu Gnome 13.10

---

