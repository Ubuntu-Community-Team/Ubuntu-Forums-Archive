---
title: "Problem with Preseed file HELP!"
date: 2006-03-21
forum: Installation &amp; Upgrades
---

### Post by aixguy on 2006-03-21
I am tying to produce an automated, unprompted, network boot and load that utilizes NO removeable media or hardrives.

So far:
Boot target install servers using PXE  
Use DHCP and tftp to provide the pexlinux.0 network install 
Edited pxlinux.cnf and added installer parameters including a preseed file.
Edited the preseed file found here [http://archive.ubuntu.com/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/apcs01.html](http://archive.ubuntu.com/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/apcs01.html)

I can boot the server and install the server version of Ubuntu with my current config.  I still get a prompted for the hostname and have not figured out how to write a recipe for the partioner but those are not bothering me.

My problem is I can not get ssh to install using the preseed file.
Using this exapmple syntax from above link
base-config	base-config/late_command	string apt-get install ssh
The install failes with a corupt preseed file.
Using this syntex
d-i	preseed/late_command		string  /usr/bin/apt-get install ssh
I get /usr/bin/apt-get not found.
So how do I customize a server install druing the install process???
I know this is uncharted water, I have been working on it for over a week and there is very little info about network installation.
I hope there is someone out there that can help with this, I would really like to be able to install linux like I do AIX.
Thanks
Doug

Preseed file
base-config     apt-setup/another       boolean false
base-config     apt-setup/country       select enter information manually
base-config     apt-setup/directory     string /ubuntu
base-config     apt-setup/hostname      string archive.ubuntu.com
base-config     apt-setup/security-updates      boolean true
base-config     apt-setup/uri_type      select http
base-config     base-config/intro       note 
base-config     base-config/login       note 
base-config     tzconfig/choose_country_zone/BR select East
base-config     tzconfig/choose_country_zone/CA select Eastern
base-config     tzconfig/choose_country_zone/US select Eastern
base-config     tzconfig/choose_country_zone_single boolean true
base-config     tzconfig/gmt            boolean true
d-i     grub-installer/only_debian      boolean true
d-i     grub-installer/with_other_os    boolean true
d-i     mirror/country          string enter information manually
d-i     mirror/http/directory   string /ubuntu
d-i     mirror/http/hostname    string archive.ubuntu.com
d-i     mirror/http/proxy       string 
d-i     mirror/suite            string breezy
d-i     netcfg/confirm_static   boolean true
d-i     netcfg/disable_dhcp     boolean true
d-i     netcfg/get_domain       string  safelite.as
d-i     netcfg/get_gateway      string 10.0.28.1
d-i     netcfg/get_hostname     string ubuntu-test
d-i     netcfg/get_ipaddress    string 10.0.28.167
d-i     netcfg/get_nameservers  string 10.0.36.200
d-i     netcfg/get_netmask      string 255.255.252.0
d-i     netcfg/wireless_wep     string 
d-i     prebaseconfig/reboot_in_progress        note 
d-i     preseed/late_command    string /usr/bin/apt-get install ssh
passwd          passwd/user-fullname            string fred
passwd          passwd/user-password            password fred234
passwd          passwd/user-password-again      password fred1234
passwd          passwd/username                 string fred


pxelinux.cfg
display ubuntu-installer/i386/boot-screens/syslinux.txt
default linux

F1 ubuntu-installer/i386/boot-screens/f1.txt
F2 ubuntu-installer/i386/boot-screens/f2.txt
F3 ubuntu-installer/i386/boot-screens/f3.txt
F4 ubuntu-installer/i386/boot-screens/f4.txt
F5 ubuntu-installer/i386/boot-screens/f5.txt
F6 ubuntu-installer/i386/boot-screens/f6.txt
F7 ubuntu-installer/i386/boot-screens/f7.txt
F8 ubuntu-installer/i386/boot-screens/f8.txt
F9 ubuntu-installer/i386/boot-screens/f9.txt
F0 ubuntu-installer/i386/boot-screens/f10.txt

label linux
        kernel ubuntu-installer/i386/linux
        append  base-config/package-selection= preseed/url=http://10.0.36.18/ubuntu/preseed debian-installer/locale=en_US kbd-chooser/method=us netcfg/choose_interface=eth0 initrd=ubuntu-installer/i386/initrd.gz ramdisk_size=16432 root=/dev/rd/0 rw  --

prompt 0
timeout 0

---

### Post by aixguy on 2006-04-05
Bump.. anyone.. anyone at all??

---

### Post by waraba on 2006-04-11
Hi AIXGUY!
In the moment I have more or less the same problem.
Do you found a solution meantime?

But I successfully wget-ed a configuration. Maybe you can wget your ssh-package and dpkg -i it. (which is not really nice)

Waraba

---

### Post by aixguy on 2006-04-11
No, I have not done anymore work on this particular area, managment has me working on other aspects of using Ubuntu in our environment.

---

### Post by tazzer on 2007-03-13
For what's worth (as time has marched on).  In Edgy it will take this in the preseed file:

d-i preseed/late_command string  \
              apt-install --force-yes mailx

Tazzer

---

