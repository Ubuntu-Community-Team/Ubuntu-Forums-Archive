---
title: "ubuntu-7.10-beta-desktop-i386 install"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by cpyct2004 on 2007-09-28
hi all..

i' ve vestel " Millenium 23708 23´´ TFT-LCD " television & Nvidia geforce 256gt agp. i' m using with ubuntu 7.04 feisty. (:guitar:)

i'm trying ubuntu-7.10-beta-desktop-i386 installing but monitor signal (desktop)  N/A.
i'm checking monitor for other picture mode but no desktop. how can i install ubuntu 7.10 :lolflag:

thanks

---

### Post by Pumalite on 2007-09-28
Try the Alternate CD.

---

### Post by Seisen on 2007-09-28
Your best bet like pumalite said is to use the Ubuntu Alternate Cd then after you have done you will have to configure you video card.

---

### Post by cpyct2004 on 2007-09-30
i'm trying alternate cd (text mode) for install.  first problem about keyboard configuration. (pass)
and second problem,  i'm receiving some errors. what is the problem i don't know. when the keyboard configuration is ok (language english) i' ve receive some errors again. my hardwares ok for ubuntu but same problem. :confused:

---

### Post by Pumalite on 2007-09-30
Detail here what you did reconf xserver with the error messages you got.

---

### Post by cpyct2004 on 2007-10-01
configuring the network with dhcp
network autoconfiguraiton failed
do not configure the network at this time continue (because wireless conneciton, pass)

....

installing the base system
debootstap warning
warning couldn't download package libncurses5
..libncursesw5
..ncurses-base
..ncurses-bin
..ntpdate

warning failure trying to run:
chroot / target /sbin/1dconfig (continue)

the debootstrap program exited with an error (return value1)
check /var/log/syslog or see virtual console 4 for the details (continue9

failed to install the base system
the base system installation in to target/failed
check /var/log/syslog or see ...

installation step failed..

install the base system... must be internet connection?
and normaly  i'm using zd1211-source driver for my wi adaptor but wireless connection N/A
at the same time, this driver can be found on synaptic manager. why not automatic install? must be manuel install?


syslog some notes..

...
ct  1 19:46:50 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Oct  1 19:46:50 10freedos: debug: /dev/sda1 is not a FAT partition: exiting
Oct  1 19:46:50 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Oct  1 19:46:50 10qnx: debug: /dev/sda1 is not a QNX4 partition: exiting
Oct  1 19:46:50 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Oct  1 19:46:50 20microsoft: debug: /dev/sda1 is not a MS partition: exiting
Oct  1 19:46:50 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Oct  1 19:46:50 30utility: debug: /dev/sda1 is not a FAT partition: exiting
.....

hdd partition problem?

thanks

---

### Post by Pumalite on 2007-10-01
Get Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
Partition ahead of time: give 10 GB to '/', 500 MB to/swap, and the rest to /home
Do md5sum on iso, burn at 4x, clean lens in your burner if necessary or download new iso. Follow these guidelines: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

