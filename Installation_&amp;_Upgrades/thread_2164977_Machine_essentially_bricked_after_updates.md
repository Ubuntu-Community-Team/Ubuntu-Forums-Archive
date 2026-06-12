---
title: "Machine essentially bricked after updates"
date: 2013-08-02
forum: Installation &amp; Upgrades
---

### Post by danbuntu2 on 2013-08-02
I have a machine with Ubuntu 13.04 that has been running fine and dandy.  I was prompted to install updates (sorry, I didn't pay attention to what they were).  Once they were installed, I rebooted, and now it freezes right when the login screen appears.  I tried booting in safe mode, recovery mode, in root shell prompt doing a
apt-get update
apt-get dist-upgrade

Nothing has worked.

---

### Post by Jonor on 2013-08-02
Try using this rather similar line :

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by QIII on 2013-08-02
Were you using a proprietary graphics driver and might one of the updates have been a new kernel?

---

### Post by oldfred on 2013-08-02
I try to pay attention to what updates are taking place so I have an idea what may break or need repair if it does not boot. 

Did you install video drivers and maybe a new kernel did not correctly update? Besides recovery mode does the next oldest kernel boot?

If you can get to command line with recovery. lines with # are comments:
 #if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
# fix Broken packages -f 
apt-get -f install
dpkg --configure -a

---

### Post by QIII on 2013-08-02
You know what they say about great minds, oldfred...

---

### Post by danbuntu2 on 2013-08-02
Thank you much Jonor.  That worked perfectly.  Also, thank you to everyone to whom provided help.  I am greatly appreciative to the Linux community!!!!

---

### Post by danbuntu2 on 2013-08-02
Solved.

---

