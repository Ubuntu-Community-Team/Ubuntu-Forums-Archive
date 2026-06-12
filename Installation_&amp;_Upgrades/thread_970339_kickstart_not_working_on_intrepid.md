---
title: "kickstart not working on intrepid"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by GarryOwen on 2008-11-04
I have been using basically the same process for doing kickstart installs for edgy, feisty, gutsy and hardy. Works Great :)
The same setup is failing for intrepid.

Basically keywords in the kickstart file are not being parsed, giving the following errors in /var/log/syslog

Nov  4 19:03:21 kickseed: Downloading kickstart file from [http://10.1.2.3/config/intrepid.cfg](http://10.1.2.3/config/intrepid.cfg)
Nov  4 19:03:21 kickseed: Reading kickstart file from /var/spool/kickseed/fetch/http/10.1.2.3/configs/intrepid.cfg
Nov  4 19:03:21 kickseed: Failed to parse rootpw options
Nov  4 19:03:21 kickseed: Failed to parse url options
Nov  4 19:03:21 kickseed: Failed to parse bootloader options
Nov  4 19:03:21 kickseed: Failed to parse clearpart options
Nov  4 19:03:21 kickseed: Failed to parse partition options

and so on. Some keywords are parsed successfully, eg.

lang en_AU
keyboard us

and the %packages section (these appear in preseed.cfg)

Has anyone else had this problem ?

My kickstart file looks like the following

lang en_AU
langsupport en_US --default=en_AU
keyboard us
timezone Australia/Brisbane
rootpw --iscrypted $1$Y9pqO8V1$htdtqLSD1ilCOvZ.jdXsx/
reboot
text
install
url --url [http://10.1.2.3/ubuntu/intrepid/](http://10.1.2.3/ubuntu/intrepid/)
bootloader --location=mbr 
zerombr yes
clearpart --all --initlabel 
part / --fstype ext3 --size 1 --grow --asprimary --ondisk sda 
part swap --size 512 --asprimary --ondisk sda 
auth  --useshadow  --enablemd5 
network --bootproto=dhcp --device=eth0
firewall --enabled --ftp --ssh --telnet --port=21:tcp
xconfig --depth=32 --resolution=1024x768 --defaultdesktop=GNOME --startxonboot
%packages
@ ubuntu-desktop
system-config-kickstart

and I am booting the vmlinuz and initrd.gz files from the netboot directory of the 8.10 alternate i386 CD

-- 
Thanks
Garry

---

### Post by phatagnus on 2008-11-04
The same thing happens here, would love to see a hint on this one.

---

### Post by dixonp on 2008-11-14
This is cause by bug #293586: lack of CONFIG_GETOPT_LONG in busybox-udeb completely breaks Kickstart.

For a workaround that makes the "url --url http://xxx" option work again, see:

[https://bugs.launchpad.net/ubuntu/+bug/293586](https://bugs.launchpad.net/ubuntu/+bug/293586)

---

