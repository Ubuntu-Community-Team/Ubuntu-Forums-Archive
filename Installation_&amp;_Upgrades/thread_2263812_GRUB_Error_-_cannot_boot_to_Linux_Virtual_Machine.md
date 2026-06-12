---
title: "GRUB Error - cannot boot to Linux Virtual Machine"
date: 2015-02-03
forum: Installation &amp; Upgrades
---

### Post by hdorath on 2015-02-03
Hello Everyone, 
I recently converted my physical server on a virtual server using VMWare converter, my physical server is running slackware and it migrated "Fine", the problem is that it wont boot due to a grub issue.
Ive been reading on the internet and Ive tried a lot of posible solutions but none of them work.
I tried installing Grub using a Ubuntu live CD and currently im stuck at the GRUB promt. 
Then, I tried installing boot-repair from the live CD and its telling that I should close all my packages manager  and then try again but im not running synaptic or anything.
Bellow you will find the output of my boot-repair try,

[http://paste.ubuntu.com/10036662/](http://paste.ubuntu.com/10036662/)

Please Help!!

Thank you,

---

### Post by oldfred on 2015-02-04
Is this a standard 14.10 install in your virtual memory?
It does not look typical, but I do not know virtual installs.

Script is not showing any kernels, which if standard install it would show, but it only looks in the normal default locations.
From Boot-Repair you can try the full uninstall/purge of grub and reinstall of grub as I think that will also reinstall the most current kernel.

Otherwise you probably have to chroot into your install and do full updates including a new kernel.
Not sure if differences to chroot into a virtual install.
       To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.

      
 drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

Chroot examples above are reinstall of grub. You may need to also include these:
      
 #Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
# fix Broken packages -f 
apt-get -f install
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
dpkg --configure -a

   sudo update-initramfs -k all -c
sudo update-grub

---

