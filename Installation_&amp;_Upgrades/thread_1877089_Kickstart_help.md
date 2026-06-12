---
title: "Kickstart help"
date: 2011-11-07
forum: Installation &amp; Upgrades
---

### Post by kidintraffic on 2011-11-07
I'm running into an issue where I'm trying to setup a network install (from a local server) with Ubuntu 11.10 using the alternate ISO.  

My kickstart file fails when I install the ubuntu-desktop package.  The error message is: > “Installation step failed. An installation step failed. You can try to  run the failing item again from the menu, or skip it and choose  something else. The failing step is: Select and install software.”                      Removing the line to install the package results in the install finishing, but only displaying a blinking cursor.  

Any recommendations on what to try/do?

Here is my kickstart file:
```

#System language
lang en_US
#Language modules to install
langsupport en_US
#System keyboard
keyboard us
#System mouse
mouse
#System timezone
timezone America/New_York
#Root password
rootpw --disabled
#Initial user
user ubuntu --fullname "Ubuntu" --iscrypted --password $1$SCOXweI4$drrBtag3Am7IBIKztnx.00
#Reboot after installation
reboot
#Use text mode install
text
#Install OS instead of upgrade
install
#Use Web installation
url --url http://server/oneiric
#System bootloader configuration
bootloader --location=mbr 
#Clear the Master Boot Record
zerombr yes
#Partition clearing information
clearpart --all --initlabel 
#Disk partitioning information
part swap --recommended 
part / --fstype ext3 --size 1 --grow 
#System authorization infomation
auth  --useshadow  --enablemd5 
#Network information
#network --bootproto=dhcp --device=eth0
network --device eth0 --bootproto dhcp
services --enabled=network
#Firewall configuration
firewall --enabled --trust=eth0 
#X Window System configuration information
xconfig --depth=32 --resolution=1024x768 --defaultdesktop=GNOME --startxonboot
#Package install information
%packages
@ ubuntu-desktop

```

---

### Post by kidintraffic on 2011-11-10
Anyone have any insight or any tips?

---

### Post by yaleman on 2012-04-21
I hope someone helped you by now, but I'll reply for the sake of it... If you get errors in the installation process, hit the "save logs" entry in the menu and it'll give you an option where to put them.

The easiest way (I find) is to select web, which will put them on a web-accessible mini site so you can browse them. You'll be looking for the syslog entry, click that and scroll to the bottom. It should tell you why the installation has failed.

---

