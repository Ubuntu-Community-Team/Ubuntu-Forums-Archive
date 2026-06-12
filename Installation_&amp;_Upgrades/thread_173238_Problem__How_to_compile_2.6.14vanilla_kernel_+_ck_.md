---
title: "Problem : How to compile 2.6.14vanilla kernel + ck patch"
date: 2006-05-10
forum: Installation &amp; Upgrades
---

### Post by eproject on 2006-05-10
i try to compile new kernel by follow how to 2.6.14 Vanilla kernel + ck Patchset like this

my labtop spec
ASUS M5200AE
Centrino 740 1.73GHz
512MB
Digital Flat Panel on Mobile intel(R) 915GM/GSM

sudo apt-get install build-essential bin86 kernel-package
sudo apt-get install libqt3-headers libqt3-mt-dev (needed for make xconfig) 
sudo cp linux-2.6.14.tar.bz2 /usr/src
cd /usr/src
sudo tar -xvjf linux-2.6.14.tar.bz2
sudo mv linux-2.6.14/ linux-2.6.14cK1
sudo rm -rf linux
sudo ln -s /usr/src/linux-2.6.14cK1 linux
cd /usr/src/linux
sudo -s -H
Password: <specify user password>
sudo bzcat /home/username/patch-2.6.14-ck1.bz2| patch -p1
sudo cp /boot/config-2.6.12-9-686 .config 
sudo make xconfig
(chang config:
In "General Setup" activate:
-Support for paging of anonymous memory (swap)
--Support for prefetching swapped memory
In "Processor type and features":
-Processor family Choose the model of your processor.
Activate:
-Preemption Model
--Voluntary Kernel Preemption (Desktop)
-High Memory Support
--off -if you have less than 1 GB of RAM
--1GB Low Memory Support -if you have 1GB of RAM
--4GB -if you have more than 1GB of RAM
-Timer frequency
--1000 Hz
In "Device drivers" go to "Block devices" and in "IO Schedulers" 
leave only the "CFQ I/O scheduler" activated, which provides the best performance.
In "Kernel hacking" uncheck "Kernel debugging".)

make-kpkg clean
make-kpkg -initrd --revision=ck1 kernel_image
sudo dpkg -i kernel-image-2.6.14*.deb
sudo reboot

but after i reboot my ubuntu ... it show me about can run new kernel
but after loading "Mounting root file system" .... it's hang, stop running and show problem

somebody can help me or suggest me about how to compile new kernel
becaue i just only patch kernel with iptable and netfilter-layet7 with 
kernel  2.6.14-2.6.15 

or somebody who success compile new kernel ... can you help me what should i do? 

thank you very much

---

