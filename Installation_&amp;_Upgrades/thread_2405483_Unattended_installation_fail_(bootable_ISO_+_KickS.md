---
title: "Unattended installation fail (bootable ISO + KickStart)"
date: 2018-11-06
forum: Installation &amp; Upgrades
---

### Post by mox- on 2018-11-06
Hi,
  I'm successfully installing RHEL/CentOS using that recipe

  (Note that this is used to build VMWare machines)

  I'm using the installation DVD to generate a custom bootable ISO file (~50MB) with hard-coded IP Address of the server (We do not have a DHCP Service on that network and are not allowed to do it, so no PXE Boot)
  The KickStart file is put on a web server.

  How it works, the automation scripts that create the VM automatically assign the ISO to the VM then boots it. The ISO boots, setup networking and load the KickStart to proceed to the installation.

  On the boot ISO, I have this isolinux file:

```

default vesamenu.c32
#prompt 1
timeout 200
display boot.msg
menu color border 0 #ffffffff #00000000
menu color sel 7 #ffffffff #ff000000
menu color title 0 #ffffffff #00000000
menu color tabmsg 0 #ffffffff #00000000
menu color unsel 0 #ffffffff #00000000
menu color hotsel 0 #ff000000 #ffffffff
menu color hotkey 7 #ffffffff #ff000000
menu color scrollbar 0 #ffffffff #00000000
label ks
menu label ^Kickstart Installation
menu default
kernel vmlinuz
append initrd=initrd ks=http://10.0.0.2/ubuntu-test.ks ip=10.0.0.5 ksdevice=eth0 netmask=255.255.255.0 gateway=10.0.0.1 dns=8.8.8.8 noverifyssl net.ifnames=0 biosdevname=0

```

  Again, this works great on RHEL7/CentOS but not on Ubuntu.

  When I boot on the generated ISO file on Ubuntu I get the following screen:

```

Warning: fsck not present, so skipping unknown file system
mount: can't find /root in /etc/fstab
done.
Begin: Running /scripts/local-bottom ... done.
Begin: Running /scripts/init-bottom ... ipconfig: 10.0.0.5: SIOCGIFINDEX: No such device
ipconfig: no devices to configure
ipconfig: 10.0.0.5: SIOCGIFINDEX: No such device
ipconfig: no devices to configure
ipconfig: 10.0.0.5: SIOCGIFINDEX: No such device
ipconfig: no devices to configure
ipconfig: 10.0.0.5: SIOCGIFINDEX: No such device
ipconfig: no devices to configure
ipconfig: 10.0.0.5: SIOCGIFINDEX: No such device
ipconfig: no devices to configure
ipconfig: 10.0.0.5: SIOCGIFINDEX: No such device
ipconfig: no devices to configure
ipconfig: 10.0.0.5: SIOCGIFINDEX: No such device
ipconfig: no devices to configure
ipconfig: 10.0.0.5: SIOCGIFINDEX: No such device
ipconfig: no devices to configure
ipconfig: 10.0.0.5: SIOCGIFINDEX: No such device
ipconfig: no devices to configure
ipconfig: 10.0.0.5: SIOCGIFINDEX: No such device
ipconfig: no devices to configure
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /dev on /root/dev failed: No such file or directory
done.
mount: mounting /run on /root/run failed: No such file or directory
run-init: current directory on the same filesystem as the root: error 0
Target filesystem doesn't have requested /sbin/init.
run-init: current directory on the same filesystem as the root: error 0
run-init: current directory on the same filesystem as the root: error 0
run-init: current directory on the same filesystem as the root: error 0
run-init: current directory on the same filesystem as the root: error 0
run-init: current directory on the same filesystem as the root: error 0
No init found. Try passing init= bootarg.


BusyBox v1.27.2 (Ubuntu 1:1.27.2-2ubuntu3) built-in shel (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

```

Looks like it's missing an interface or something, but when I type **ip a** I see the **eth0** device

Anyone have experience generating bootable ISO file with genisoimage and can help me with that issue?

 Thanks,

 --Ben

---

