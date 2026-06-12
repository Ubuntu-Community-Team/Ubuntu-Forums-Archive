---
title: "error while updating"
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by mangkusapi on 2008-12-02
dear all,

i am a newbie on linux ubuntu..im using ubuntu Linux 8.10. while updating, there is an error on E: /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb: unable to make backup link of `./boot/vmlinuz-2.6.27-7-generic' before installing new version

because of this, there are several application failed to updating. please help me to fixed this problem. thanks

piss

---

### Post by lemming465 on 2008-12-03
Run *df -m* and *df -i* to check that you have both free disk space and free inodes on /var.  Run *sudo apt-get clean* to clean out the offending cached packages, and then retry *sudo apt-get update* to refresh your package lists and *sudo apt-get upgrade* to install the pending stuff.  If that doesn't solve it, write back with any error messages you got.

---

### Post by Ricardus on 2008-12-04
I'm having similar problems.  I had a few packages that said they didn't install properly during the install, and the installer itself said it was aborting near the very end of the install, but my machine it running, and it says it's running version 8.04.1.

 However there is one greyed out package that it won't install.  Here was the last command I executed at the advice of someone up here:

sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libgtk1.2
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


 Why is that package being "kept back" ??

---

### Post by lemming465 on 2008-12-04
> Why is {libgtk1.2} being "kept back" ??
Beats me.  Does **sudo apt-get upgrade --fix-broken** improve the situation any?

---

### Post by Ricardus on 2008-12-04
No, it didn't fix it.

sudo apt-get upgrade --fix-broken
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libgtk1.2
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

---

