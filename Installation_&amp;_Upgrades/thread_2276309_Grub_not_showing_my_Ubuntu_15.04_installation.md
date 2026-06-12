---
title: "Grub not showing my Ubuntu 15.04 installation"
date: 2015-05-01
forum: Installation &amp; Upgrades
---

### Post by jspice6 on 2015-05-01
Hey guys so today I rebooted from my installation of 15.04 and when I was greeted by grub I saw all of my partitions except for Ubuntu 15.04 . It changed the default boot to Windows 7. I tried updating grub from two of my other installs (Mint and Xubuntu) but neither worked. However when I run update-grub it shows ubuntu 15.04, but it never apears on the grub menu after reboot. I have tried every method i have seen on the forum so far and am wondering if there is some manual way to edit the grub file to make sure ubuntu shows up. Thanks

---

### Post by oldfred on 2015-05-01
Is grub menu full and you have to scroll down to see bottom. Tiny arrow in lower right corner may tell you that.

Otherwise post this. Do not run any auto fix until reviewed.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by jspice6 on 2015-05-01
Hi thanks for the reply here is the result: [http://paste.ubuntu.com/10964252/](http://paste.ubuntu.com/10964252/)

---

### Post by oldfred on 2015-05-01
Other grub installs search for grub.cfg to find boot stanzas to add. Your install in sda5 shows no kernels or Ubuntu boot entries. But your burg.cfg does. Other grub will not search burg as it is old and not used much. And your burg entries show kernels like 3.13 which is more from 14.04.

Did kernels get deleted from that install?
You can use boot repair and choose the install in sda5. A full chroot and uninstall/reinstall of grub should also add one new kernel. If not you may have to add it also.

---

### Post by jspice6 on 2015-05-01
So I can chroot to my sda5 partition and reinstall grub there?

---

### Post by oldfred on 2015-05-01
Boot-Repair walks you thru a minimal chroot. It seems you need the kernels and possibly a grub update.

Otherwise:
       drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)


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

