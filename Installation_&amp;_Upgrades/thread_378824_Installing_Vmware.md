---
title: "Installing Vmware"
date: 2007-03-07
forum: Installation &amp; Upgrades
---

### Post by darkenemy on 2007-03-07
im having a problem installing vmware on my ubuntu 6.10
 
when i type > sudo '/home/darkenemy/Desktop/vmware-player-distrib/vmware-install.pl' 

into the therminal,
i get

> 
Creating a new installer database using the tar3 format.

Installing the content of the package.

In which directory do you want to install the binary files? 
[/usr/bin] 

What is the directory that contains the init directories (rc0.d/ to rc6.d/)? 
[/etc] 

What is the directory that contains the init scripts? 
[/etc/init.d] 

Unable to copy the source file ./installer/services.sh to the destination file 
/etc/init.d/vmware.

Execution aborted.


for the life of me i cant get this to work.  can anyone help?

---

### Post by andreas64 on 2007-03-08
Hi,

cd /home/darkenemy/Desktop/vmware-player-distrib
sudo ./vmware-install.pl

Andreas

---

