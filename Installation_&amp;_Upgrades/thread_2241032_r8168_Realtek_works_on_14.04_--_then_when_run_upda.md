---
title: "r8168 Realtek works on 14.04 -- then when run updates - I loose networking"
date: 2014-08-23
forum: Installation &amp; Upgrades
---

### Post by xigen on 2014-08-23
I have been having issues with 14.04 64 bit ubuntu and r8169.

I replaced realtek r8169 with r8168
[http://ubuntuforums.org/showthread.php?t=2240533&page=3&p=13106182#post13106182](http://ubuntuforums.org/showthread.php?t=2240533&page=3&p=13106182#post13106182)

Networking worked.  All was good.

Then I installed updates - and my network did not connect

Then I tried to do exactly what I did on a fresh install of ubuntu 14.04

I went to Downloads - unpacked the file - and as instructed:  sudo ./autorun.sh 

unfortunately - my networking did not work.    

How do I see what is going wrong and fix it?

_____________________

```

meow@MeowBatunde:~/Downloads$ cd r8168-dkms-8.038.00/
meow@MeowBatunde:~/Downloads/r8168-dkms-8.038.00$ !17
sudo ./autorun.sh
[sudo] password for meow: 

Check old driver and unload it.
Build the module and install
Can't read private key
Backup r8169.ko
rename r8169.ko to r8169.bak
DEPMOD 3.13.0-34-generic
load module r8168
modprobe: ERROR: could not insert 'r8168': Exec format error
Updating initramfs. Please wait.
update-initramfs: Generating /boot/initrd.img-3.13.0-34-generic
Completed.


2nd try with same driver ...

meow@MeowBatunde:~/Downloads$ ls
3005217-r8168-dkms-8.038.00.tar.gz  r8168-dkms-8.038.00
dkms_2.2.0.3-1.1ubuntu5_all.deb
meow@MeowBatunde:~/Downloads$ cd r8168-dkms-8.038.00/
meow@MeowBatunde:~/Downloads/r8168-dkms-8.038.00$ ls
autorun.sh  dkms.conf  Makefile  README  src
meow@MeowBatunde:~/Downloads/r8168-dkms-8.038.00$ sudo ./autorun.sh 
[sudo] password for meow: 

Check old driver and unload it.
Build the module and install
Can't read private key
DEPMOD 3.13.0-34-generic
load module r8168
modprobe: ERROR: could not insert 'r8168': Exec format error
Updating initramfs. Please wait.
update-initramfs: Generating /boot/initrd.img-3.13.0-34-generic
Completed.
meow@MeowBatunde:~/Downloads/r8168-dkms-8.038.00$ 


```

---

### Post by xigen on 2014-08-23
from the terrific phrasodym:

Uninstall, reboot, install realtek r8168 again. 

```

sudo dkms remove -m r8168-dkms -v 8.038.00 --all
sudo rm -r /usr/src/r8168-dkms-8.038.00

```

---

