---
title: "Cannot complete update manager process"
date: 2012-09-22
forum: Installation &amp; Upgrades
---

### Post by StepNjump on 2012-09-22
Hi,

I get the following error message when attempting to download the updates from the update manager. 

Error message: **_Failed to download package files -  Check your Internet connection._**
If someone could help me with this, I would appreciate it a lot.

However, my internet connection works just fine as usual.

Thanks in advance for your help all.


ATC


lsb_release -a
LSB Version:	core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 11.04
Release:	11.04
Codename:	natty

ERROR MESSAGE details:
Failed to fetch [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/pool/main/n/nvidia-graphics-drivers/nvidia-current_302.17-0ubuntu1~natty~xup1_i386.deb](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/pool/main/n/nvidia-graphics-drivers/nvidia-current_302.17-0ubuntu1~natty~xup1_i386.deb) 404  Not Found
Failed to fetch [http://dl.google.com/linux/chrome/deb/pool/main/g/google-chrome-stable/google-chrome-stable_20.0.1132.43-r143823_i386.deb](http://dl.google.com/linux/chrome/deb/pool/main/g/google-chrome-stable/google-chrome-stable_20.0.1132.43-r143823_i386.deb) 404  Not Found [IP: 74.125.228.38 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/clamav/libclamav6_0.97.5+dfsg-1ubuntu0.11.04.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/clamav/libclamav6_0.97.5+dfsg-1ubuntu0.11.04.2_i386.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/clamav/clamav-base_0.97.5+dfsg-1ubuntu0.11.04.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/c/clamav/clamav-base_0.97.5+dfsg-1ubuntu0.11.04.2_all.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/clamav/clamav-freshclam_0.97.5+dfsg-1ubuntu0.11.04.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/clamav/clamav-freshclam_0.97.5+dfsg-1ubuntu0.11.04.2_i386.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/clamav/clamav_0.97.5+dfsg-1ubuntu0.11.04.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/clamav/clamav_0.97.5+dfsg-1ubuntu0.11.04.2_i386.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-globalmenu_13.0.1+build1-0ubuntu0.11.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-globalmenu_13.0.1+build1-0ubuntu0.11.04.1_i386.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_13.0.1+build1-0ubuntu0.11.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_13.0.1+build1-0ubuntu0.11.04.1_i386.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_13.0.1+build1-0ubuntu0.11.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_13.0.1+build1-0ubuntu0.11.04.1_i386.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-en_13.0.1+build1-0ubuntu0.11.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-en_13.0.1+build1-0ubuntu0.11.04.1_i386.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://dl.google.com/linux/talkplugin/deb/pool/main/g/google-talkplugin/google-talkplugin_3.1.4.0-1_i386.deb](http://dl.google.com/linux/talkplugin/deb/pool/main/g/google-talkplugin/google-talkplugin_3.1.4.0-1_i386.deb) 404  Not Found [IP: 74.125.228.38 80]
Failed to fetch [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/pool/main/n/nvidia-settings/nvidia-settings_302.17-0ubuntu1~natty~xup3_i386.deb](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/pool/main/n/nvidia-settings/nvidia-settings_302.17-0ubuntu1~natty~xup3_i386.deb) 404  Not Found
Failed to fetch [http://deb.opera.com/opera/pool/non-free/o/opera/opera_12.00.1467_i386.deb](http://deb.opera.com/opera/pool/non-free/o/opera/opera_12.00.1467_i386.deb) 404  Not Found

---

### Post by lincoln32 on 2012-09-22
open a termainal copy paste each command and post back any errors

sudo apt-get update 

sudo apt-get upgrade

sudo apt-get distro-upgrade

---

### Post by StepNjump on 2012-09-22
Hi Lincoln,

Thank you very much for getting back to me so quickly.
In the upgrade process, I got errors... with the nvidia
Looks like the system is correcting those...

I will get back to you shortly.

SnJ

---

### Post by StepNjump on 2012-09-22
Ok Lincoln,

It looks like I could only successfully run the first command.

Here are the results:

sudo apt-get update
result: Fetched 1,734 kB in 5s (297 kB/s)
Reading package lists... Done

sudo apt-get upgrade
Setting up koffice (1:2.3.3-0ubuntu4.1) ...
Setting up libmono-system-web2.0-cil (2.6.7-5ubuntu3.1) ...
Setting up libmono-wcf3.0-cil (2.6.7-5ubuntu3.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Processing triggers for python-central ...
Errors were encountered while processing:
 nvidia-173
 nvidia-current
E: Sub-process /usr/bin/dpkg returned an error code (1)

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  icedtea-netx icedtea-plugin icedtea6-plugin linux-generic
  linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up nvidia-173 (173.14.30-0ubuntu1.2) ...
dpkg: error processing nvidia-173 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up nvidia-current (304.43-0ubuntu1~natty~xup1) ...
update-alternatives: error: alternative link /usr/share/man/man1/nvidia-xconfig.1.gz is already managed by i386-linux-gnu_gl_conf.
dpkg: error processing nvidia-current (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 nvidia-173
 nvidia-current
E: Sub-process /usr/bin/dpkg returned an error code (1)

Hope this helps. THanks

---

### Post by StepNjump on 2012-09-22
Lincoln, would it be advisable to proceed with following commands that I found on a forum a few minutes ago...

sudo apt-get remove --purge nvidia-current dkms

then

sudo apt-get update
sudo apt-get install dkms nvidia-current

Would it risk to blank my screen completely?
What do you think?

---

### Post by StepNjump on 2012-09-29
Lincoln, thank you very much for your help. I finally had it fixed after months of issues...
ikonia from irc.ubuntu actually pointed me in the right direction:

By removing the checkmarks to prevent NVIDIA products to update (supposedly the NVIDIA applications were no longer available from the Ubuntu repos), this allowed the system to install all the other updates normally.

Thank you both for your help gentlemen.


Pete, StepNjump.

---

