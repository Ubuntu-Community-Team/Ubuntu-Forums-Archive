---
title: "Recover Interrupted Ubuntu Upgrade from 14.04 LTS to 16.04 LTS"
date: 2018-07-16
forum: Installation &amp; Upgrades
---

### Post by coolcatco888 on 2018-07-16
Hi All,

My initial upgrade seemed to fail when during the upgrade the screen turned black and never recovered after 20mins.  I rebooted and then after a painful process of trial and error I was finally able to execute this command to update the distro:
```
apt-get dist-upgrade
```
(I was using this guide as reference: [how-to-repair-ubuntu-installation-after-interrupted-dist-upgrade-without-losing]("https://askubuntu.com/questions/748289/how-to-repair-ubuntu-installation-after-interrupted-dist-upgrade-without-losing"))

I'm pretty sure my version is now 16.04 LTS as a mew image: 4.4.0-130-generic was added to GRUB2.  **However I cannot boot, instead, it tries to boot, fails and brings me to the recovery console.**

To fix this, I type:
```
apt-get update
apt-get -f install
```

I get this message:
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

So then I do exactly that and this happens
```
dpkg --configure -a
Setting up snapd (2.32.9) ...

```

**Then crashes unexpectedly with no error and then exits the console session with this message:**
```
Welcome to emergency mode! After logging in, type "journalctl -xb" to view
system logs, "systemctl reboot" to reboot, "systemctl default" or ^D to try again to boot into default mode.
Press Enter for maintenance
(or press Control-D to continue):
```

dpkg fails to configure snapd and I have no way of running **apt-get -f install**

**How do I fix my interrupted Ubuntu upgrade?  Do I:**
1. Remove the snapd package? (I'm sure it is not required)
2. Fix snapd package somehow?

Any help would be appreciated.  Also reformatting and a clean install is out of the question as I triple boot with Mac, Windows and Ubuntu on a hybrid/mbr gpt partition scheme and I literally have no way to back up my hard drive before reformatting everything.

---

### Post by coolcatco888 on 2018-07-17
Ok so I managed to solve this by myself.

I used the livecd session instead of the boot recovery session and ran:
dpkg --configure -a
apt-get update
apt-get -f install

When I rebooted, it failed to boot because I auto mounting my network drives were failing.

So I simply commented out those entries in /etc/fstab and it worked!

---

