---
title: "dpkg calling for a generic that is not installed"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by billo38 on 2008-03-07
I received notification that updates were available.  I attempted to run the update app.but received the following error message: "...run dpkg --configure -a..."  When I did that another error message indicated that dpkg could not find 2.6.20-15-generic.  That "20-15" version has never been installed on my machine.  I am currently running on 2.6.22-14-generic, and 2.6.20-16-generic was the previous installed generic.
What do I do to get past this problem?   Thanks

---

### Post by wolfen69 on 2008-03-07
go to system>admin>software sources and make sure cdrom is enabled. insert ubuntu cd and run sudo dpkg --configure -a

---

### Post by billo38 on 2008-03-08
I followed your instructions:  cdrom is mounted, i am using a terminal.  I entered sudo dpkg --configure -a and the system responds with "root@bill-desktop:~# dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.20-15-generic
Cannot find /lib/modules/2.6.20-15-generic
update-initramfs: failed for /boot/initrd.img-2.6.20-15-generic
dpkg: subprocess post-installation script returned error exit status 1"
root@bill-desktop:~# 
suggestions?
Bill

---

