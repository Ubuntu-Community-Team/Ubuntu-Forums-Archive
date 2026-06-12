---
title: "Ridiculously difficult to recover if your Distribution upgrade is interrupted!"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by Amurko on 2010-10-20
So for some unknown reason, after running the distribution upgrade and in the middle of installing files the distribution upgrade to 10.10 stops and my computer logs out without me authorizing it or doing anything at all!

WTF!

I then find myself at the login screen and the computer hard locks.

Now restarting is the only option.

So I restart and it complains the nvidia drivers are not correctly installed and locks up trying to boot up X.

Tried having Ubuntu start up using an older kernel..  same thing.

Even tried restarting in recovery mode, even that freezes!!!!!

Now the only choice left is to boot from a live cd!

There's gotta be an easier way to recover if your installation is hosed just cause your computer malfunctions while the distribution is being upgraded!!!!!!!:mad:

Suggestion for future versions: There's gotta be a button you can click when booting with the Live CD that allows you to repair an existing installation so it'll boot again!!!!!!!

---

### Post by oldfred on 2010-10-21
From the liveCD you can chroot into your system, so then you can run updates.

kansasnoob oneline chroot ------------------------------
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)
Neat huh? Added sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

kansasnoob's change sda5 to correct partition (needs change if separate /boot):

sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

Commands once in chroot:
#Then run whatever other commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories & 
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

sudo apt-get install nvidia-current nvidia-settings
sudo nvidia-xconfig


Good example of chroot and grub reinstall by drs305
[http://ubuntuforums.org/showthread.php?t=1573100](http://ubuntuforums.org/showthread.php?t=1573100)

---

### Post by Amurko on 2010-10-21
> **oldfred said:**
> From the liveCD you can chroot into your system, so then you can run updates.

kansasnoob oneline chroot ------------------------------
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)
Neat huh? Added sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

kansasnoob's change sda5 to correct partition (needs change if separate /boot):

sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

Commands once in chroot:
#Then run whatever other commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories & 
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

sudo apt-get install nvidia-current nvidia-settings
sudo nvidia-xconfig


Good example of chroot and grub reinstall by drs305
[http://ubuntuforums.org/showthread.php?t=1573100](http://ubuntuforums.org/showthread.php?t=1573100)

Need a button that does all of that when pressed!  No one has the sanity / patience to stay calm and look up info like this to do all of that when their computer won't even boot!

---

