---
title: "Mdadm 7.04 problems"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by Sierra_Dave on 2007-11-14
Hi,

I received an error message relative to mdadm on the install and now my system runs slower than with 6.4.  I upgraded to 7.04 using the update manager and it referenced a readme file that I tried to implement.  But I am running on a simple box with a single hdd and no raid or other devices.  I tried this w/o success:

bob@bob-desktop:~$ sudo
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
bob@bob-desktop:~$ sudo bob
Password:
sudo: bob: command not found
bob@bob-desktop:~$  rm -f /var/lib/mdadm/CONF-UNCHECKED
rm: cannot remove `/var/lib/mdadm/CONF-UNCHECKED': Permission denied
bob@bob-desktop:~$ sudo  rm -f /var/lib/mdadm/CONF-UNCHECKED
bob@bob-desktop:~$ sudo update-initramfs -u -k all
update-initramfs: Generating /boot/initrd.img-2.6.20-16-386
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
W: mdadm: no arrays defined in configuration file.
W: mdadm: falling back to emergency procedure in initramfs.
update-initramfs: Generating /boot/initrd.img-2.6.17-12-386

Any ideas?  
Thanks!:confused:

---

### Post by ian dobson on 2007-11-14
Hi,

Why not just deinstall mdadm. something like:-

sudo apt-get remove mdadm.

Regards
Ian Dobson

---

