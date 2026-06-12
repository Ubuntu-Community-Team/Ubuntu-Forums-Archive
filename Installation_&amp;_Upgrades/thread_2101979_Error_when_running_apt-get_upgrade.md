---
title: "Error when running apt-get upgrade"
date: 2013-01-05
forum: Installation &amp; Upgrades
---

### Post by madmarv0 on 2013-01-05
I'm getting the following error when I apt-get upgrade:


```
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.32-45-generic-pae_2.6.32-45.101_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```But, I don't know how to troubleshoot this.  When I run dpkg --configure -a, I get this message:

```
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-2.6.32-45-generic-pae; however:
  Package linux-image-2.6.32-45-generic-pae is not installed.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 2.6.32.45.52); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-generic-pae
 linux-generic-pae
```When I run apt-get install -f, I get:

```
Reading package lists...
Building dependency tree...
Reading state information...
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-33-generic-pae linux-headers-2.6.32-28-generic-pae
  linux-headers-2.6.32-31 linux-headers-2.6.32-32 linux-headers-2.6.32-33
  linux-headers-2.6.32-28 linux-headers-2.6.32-34 linux-headers-2.6.32-40
  linux-headers-2.6.32-35 linux-headers-2.6.32-41 linux-headers-2.6.32-36
  linux-headers-2.6.32-42 linux-headers-2.6.32-37 linux-headers-2.6.32-43
  linux-headers-2.6.32-38 linux-headers-2.6.32-44 linux-headers-2.6.32-39
  linux-headers-2.6.32-42-generic-pae linux-headers-2.6.32-37-generic-pae
  linux-headers-2.6.32-34-generic-pae linux-headers-2.6.32-31-generic-pae
  linux-headers-2.6.32-43-generic-pae linux-headers-2.6.32-38-generic-pae
  linux-headers-2.6.32-40-generic-pae linux-headers-2.6.32-35-generic-pae
  linux-headers-2.6.32-32-generic-pae linux-headers-2.6.32-44-generic-pae
  linux-headers-2.6.32-39-generic-pae linux-headers-2.6.32-41-generic-pae
  linux-headers-2.6.32-36-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-2.6.32-45-generic-pae
Suggested packages:
  fdutils linux-doc-2.6.32 linux-source-2.6.32 linux-tools
The following NEW packages will be installed:
  linux-image-2.6.32-45-generic-pae
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/32.0MB of archives.
After this operation, 98.3MB of additional disk space will be used.
Do you want to continue [Y/n]? (Reading database ...
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 405218 files and directories currently installed.)
Unpacking linux-image-2.6.32-45-generic-pae (from .../linux-image-2.6.32-45-generic-pae_2.6.32-45.101_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.32-45-generic-pae_2.6.32-45.101_i386.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./boot/vmlinuz-2.6.32-45-generic-pae': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-44-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-44-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-43-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-43-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-42-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-42-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-41-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-41-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-40-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-40-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-39-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-39-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-38-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-38-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-37-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-37-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-36-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-36-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-35-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-35-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-34-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-34-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-33-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-33-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-32-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-32-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-31-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-31-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-28-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-28-generic-pae
Found memtest86+ image: /memtest86+.bin
done
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.32-45-generic-pae_2.6.32-45.101_i386.deb
```Here /etc/apt/sources.list

```

#
# deb cdrom:[Ubuntu-Server 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1)]/ lucid main restricted

#deb cdrom:[Ubuntu-Server 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://download.webmin.com/download/repository sarge contrib
deb http://webmin.mirror.somersettechsolutions.co.uk/repository sarge contrib

```

---

### Post by efflandt on 2013-01-06
I normally simply do automatic updates in Ubuntu.

But it is my understanding from reading **man apt-get** while using that to upgrade an arm version of Debian wheezy (Raspbian) on a Raspberry Pi, that **apt-get upgrade** only upgrades existing packages without removing old packages or dependencies or resolving new dependencies. Many people "misuse" apt-get upgrade and end up unable to upgrade certain packages whose dependencies have changed.

To resolve changing dependencies for upgrades you should instead use:
```
sudo apt-get update && sudo apt-get dist-upgrade
```That is what I always do for Raspbian, and the only time that failed was after a spontaneous reboot during overclock testing corrupted its boot SD.

However, you have a different problem that you need to fix "**No space left on device**".  Run **df** to see which device is more than 95% full?

---

### Post by madmarv0 on 2013-01-06
Here's the output of **df**. Only /boot is full.  I'm not suer how to resize partitions.

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/linux2-root
                     285263392   4126676 266646092   2% /
none                    500316       260    500056   1% /dev
none                    504924         0    504924   0% /dev/shm
none                    504924       576    504348   1% /var/run
none                    504924         0    504924   0% /var/lock
none                    504924         0    504924   0% /lib/init/rw
none                 285263392   4126676 266646092   2% /var/lib/ureadahead/debugfs
/dev/sda1               233191    230966         0 100% /boot
/dev/mapper/linux2-hd2
                     479937288  67919432 387638464  15% /hd2

```

---

### Post by fdrake on 2013-01-06
> **madmarv0 said:**
> Here's the output of **df**. Only /boot is full.  I'm not suer how to resize partitions.

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/linux2-root
                     285263392   4126676 266646092   2% /
none                    500316       260    500056   1% /dev
none                    504924         0    504924   0% /dev/shm
none                    504924       576    504348   1% /var/run
none                    504924         0    504924   0% /var/lock
none                    504924         0    504924   0% /lib/init/rw
none                 285263392   4126676 266646092   2% /var/lib/ureadahead/debugfs
/dev/sda1               233191    230966         0 100% /boot
/dev/mapper/linux2-hd2
                     479937288  67919432 387638464  15% /hd2

```

what's the total?
```

df --total -hT


```

---

### Post by madmarv0 on 2013-01-06
Here is the **df --total**.

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/linux2-root
                     285263392   4126840 266645928   2% /
none                    500316       260    500056   1% /dev
none                    504924         0    504924   0% /dev/shm
none                    504924       576    504348   1% /var/run
none                    504924         0    504924   0% /var/lock
none                    504924         0    504924   0% /lib/init/rw
none                 285263392   4126840 266645928   2% /var/lib/ureadahead/debugfs
/dev/sda1               233191    230966         0 100% /boot
/dev/mapper/linux2-hd2
                     479937288  67919432 387638464  15% /hd2
total                1053217275  76404914 923449496   8%

```

---

### Post by fdrake on 2013-01-06
do you have many unused kernel? try to remove the odest one(s) first

[http://www.liberiangeek.net/2012/10/remove-old-kernels-from-ubuntu-12-10-with-ubuntu-tweak/](http://www.liberiangeek.net/2012/10/remove-old-kernels-from-ubuntu-12-10-with-ubuntu-tweak/)

---

### Post by fdrake on 2013-01-06
to check how many kernels have been instlled :
```

 dpkg --list | grep linux-image

```

---

### Post by madmarv0 on 2013-01-06
Thank you for your help Fdrake.  I'm trying to remove the images through the command line.  I didn't install x-windows on this box.

I'm running  

```
apt-get --dry-run remove linux-image-2.6.32-28-generic-pae
```and I'm still getting the same error message.  I think **apt-get** is borked until I free up some space on /boot.

Here's the result of **dpkg-llist |grep linux-image**.  

2.6.32-28 is the oldest one and should be safe to remove right?

```
ii  linux-image-2.6.32-28-generic-pae   2.6.32-28.55                      Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-31-generic-pae   2.6.32-31.61                      Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-32-generic-pae   2.6.32-32.62                      Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-33-generic-pae   2.6.32-33.72                      Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-34-generic-pae   2.6.32-34.77                      Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-35-generic-pae   2.6.32-35.78                      Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-36-generic-pae   2.6.32-36.79                      Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-37-generic-pae   2.6.32-37.81                      Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-38-generic-pae   2.6.32-38.83                      Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-39-generic-pae   2.6.32-39.86                      Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-40-generic-pae   2.6.32-40.87                      Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-41-generic-pae   2.6.32-41.94                      Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-42-generic-pae   2.6.32-42.96                      Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-43-generic-pae   2.6.32-43.97                      Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-44-generic-pae   2.6.32-44.98                      Linux kernel image for version 2.6.32 on x86
iU  linux-image-generic-pae             2.6.32.45.52                      Generic Linux kernel image
```

---

### Post by fdrake on 2013-01-06
> **madmarv0 said:**
> Thank you for your help Fdrake.  I'm trying to remove the images through the command line.  I didn't install x-windows on this box.

I'm running  

```
apt-get --dry-run remove linux-image-2.6.32-28-generic-pae
```and I'm still getting the same error message.  I think **apt-get** is borked until I free up some space on /boot.

Here's the result of **dpkg-llist |grep linux-image**.  

2.6.32-28 is the oldest one and should be safe to remove right?

```
ii  linux-image-2.6.32-28-generic-pae   2.6.32-28.55                      Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-31-generic-pae   2.6.32-31.61                      Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-32-generic-pae   2.6.32-32.62                      Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-33-generic-pae   2.6.32-33.72                      Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-34-generic-pae   2.6.32-34.77                      Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-35-generic-pae   2.6.32-35.78                      Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-36-generic-pae   2.6.32-36.79                      Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-37-generic-pae   2.6.32-37.81                      Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-38-generic-pae   2.6.32-38.83                      Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-39-generic-pae   2.6.32-39.86                      Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-40-generic-pae   2.6.32-40.87                      Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-41-generic-pae   2.6.32-41.94                      Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-42-generic-pae   2.6.32-42.96                      Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-43-generic-pae   2.6.32-43.97                      Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-44-generic-pae   2.6.32-44.98                      Linux kernel image for version 2.6.32 on x86
iU  linux-image-generic-pae             2.6.32.45.52                      Generic Linux kernel image
```

WOW!! you got a lot of kernels. May I suggest you first to test and then choose the one you want to keep. One day you'll need to rely on a stable one. :D  

Let us know if by removing few kernels you are able to upgrade.

---

### Post by madmarv0 on 2013-01-06
Can I just go into /boot from the command line and 

```
rm -f *2.6.32-28*
```

Is that safe?

---

### Post by fdrake on 2013-01-06
> **madmarv0 said:**
> Can I just go into /boot from the command line and 

```
rm -f *2.6.32-28*
```

Is that safe?

It is very tempting, but I would not do that ,I think, since grub and the package manager need to be reconfigured.

remove kernel using the command line
[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

simple way (one by one):[http://www.cyberciti.biz/faq/proper-way-to-remove-old-linux-kernels/](http://www.cyberciti.biz/faq/proper-way-to-remove-old-linux-kernels/)
```

sudo apt-get remove linux-image-2.6.32-28-generic-pae

```

---

### Post by fdrake on 2013-01-06
> **madmarv0 said:**
> 
I'm running  

```
apt-get --dry-run remove linux-image-2.6.32-28-generic-pae
```and I'm still getting the same error message.  I think **apt-get** is borked until I free up some space on /boot.

Here's the result of **dpkg-llist |grep linux-image**.  

2.6.32-28 is the oldest one and should be safe to remove right?


well if you cannot remove them; move a cople fro m the /boot partition to your hame (just keep the in case of error ) and see if that frees your spaces. You may want to rebbot..

---

### Post by madmarv0 on 2013-01-06
Ok, I think I've got it. In case someone else messes up their system like I did here's the final steps that fixed my problem.


[LIST=1]
[*]Run **dpkg --remove linux-image-2.6.32-28-generic-pae** (or insert the oldest kernel numbers on your particular system in place of 2.6.32-28) and that gets your foot in the door.
[*]Run **apt-get autoremove**.  There should now be enough room for the normal apt-get to free up more space.
[*]Run **apt-get install -f** to fix the dependency problems and now **apt-get upgrade** should work normally.
[/LIST]

Thanks for all the help.

---

### Post by fdrake on 2013-01-06
make sure you mark the thread as Solved for reference for other ppl

---

