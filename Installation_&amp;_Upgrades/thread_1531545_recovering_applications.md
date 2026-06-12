---
title: "recovering applications"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by kx7 on 2010-07-15
hi all...

well... i am using ubuntu 9.10

I had python2.6 installed on my laptop.. I installed python3.1, and removed python2.6.. and it did not go as i had hoped!!

currently.. most (nearly all) of my applications are removed (with 700 mb of free space generated!!)..
Is there any way to recover them??

even the applications from preferences and administration menu are missing.. any way to get those back..??

---

### Post by oldfred on 2010-07-15
DO NOT ever uninstall python 2.6. Almost all of Ubuntu runs on it.

It used to be you could not even boot to a command line or get on the internet without python. Can you boot to a command line.

Generally you need to boot from a CD or USB live and chroot into your system and reinstall everything.

kansasnoob------------------------------
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)
Neat huh?
Added sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

kansasnoob's change sda5 to correct partition
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

Once cdrooted:
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
# reinstall desktop
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop

I do not know for sure if above will reinstall python but I would think it is a depenancy of something and would be installed.
apt-get install python

---

