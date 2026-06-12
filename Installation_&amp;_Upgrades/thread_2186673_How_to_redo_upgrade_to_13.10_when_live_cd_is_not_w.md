---
title: "How to redo upgrade to 13.10 when live cd is not working?"
date: 2013-11-08
forum: Installation &amp; Upgrades
---

### Post by peterdm on 2013-11-08
I recently upgraded 13.04 to 13.10, but the upgrade broke down about 2/3rd of the way because there was not enough space in /boot.
I remembered that /boot is a separate (small) partition, and it got filled up with lots of old kernel images.
I cleaned up the old kernel images, hoping I could just redo/continue de upgrade afterwards, but no sigar.
I believe the reason to be that Ubuntu thinks it's already on 13.10 (it says so everywhere).
At this point, my system works, but I get several error dialogs after I login. I have the impression this is caused by a mixture of upgraded and non-upgraded packages.
The update manager thinks there is nothing to upgrade. For over a week... I find that very suspicious.

Then I wanted to repair the broken installation from the live cd: I burnt image ubuntu-13.10-desktop-amd64.iso.
It kernel panics upon boot, so that's also a dead end.

Finally my question: how can I convince my system to redo the upgrade all over again, _without_ using a live cd?

---

### Post by oldfred on 2013-11-08
You really need a working live DVD or flash drive, just in case things get worse and you have to reinstall or chroot into your system to fix it.

Did you verify download was good?
 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
      
 [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I normally post these commands after a chroot when you would not need sudo. Each needs sudo or you can use sudo -i. Text after # is comment, do not copy and paste that.

 #Commands once in chroot:
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

