---
title: "[SOLVED] Preseed install of alternate feisty includes openoffice.org-writer AARRGGHH!"
date: 2007-07-25
forum: Installation &amp; Upgrades
---

### Post by bazzer on 2007-07-25
Hi all.
This is driving me nuts. I've preseeded a 'hands off' install of Feisty, and no matter what, Openoffice.org-writer gets installed every time! I can't work out what is causing this - any ideas?

My preseed file:
```
base-config base-config/intro note 

base-config base-config/login note 

d-i languagechooser/language-name string English
d-i languagechooser/language-name-fb string English
d-i languagechooser/language-name-ascii string English
d-i countrychooser/shortlist string GB
d-i console-keymaps-at/keymap string uk

d-i netcfg/choose_interface select auto

d-i netcfg/wireless_wep string 

d-i partman-auto/disk string /dev/sda 
d-i partman-auto/method string regular 
d-i partman-auto/purge_lvm_from_device boolean true 
d-i partman-lvm/confirm boolean true 
d-i partman-auto/choose_recipe select Separate /home partition 
d-i partman/confirm_write_new_label boolean true 
d-i partman/choose_partition select Finish partitioning and write changes to disk 
d-i partman/confirm boolean true 


d-i grub-installer/only_debian boolean true 

d-i prebaseconfig/reboot_in_progress note 



d-i clock-setup/utc boolean false

d-i passwd/root-login boolean false
d-i passwd/user-fullname string Systems

d-i passwd/username string systems

d-i passwd/user-password-crypted password $a_hashed_password_here


base-config apt-setup/uri_type select cdrom

base-config apt-setup/another boolean false

base-config apt-setup/security-updates boolean false

popularity-contest popularity-contest/participate boolean false


base-config base-config/package-selection string 

xserver-xorg xserver-xorg/autodetect_monitor boolean true 
xserver-xorg xserver-xorg/config/monitor/lcd boolean true 
xserver-xorg xserver-xorg/config/monitor/selection-method select medium 
xserver-xorg xserver-xorg/config/monitor/mode-list select 1024x768 @ 60 Hz 

exim4-config exim4/dc_eximconfig_configtype select no configuration at this time 

exim4-config exim4/no_config boolean true 

exim4-config exim4/dc_postmaster string 

d-i preseed/late_command string wget ftp://user:password@server/home/blahblah/install.sh -O /target/root/install.sh; chmod 777 /target/root/install.sh;
```

---

### Post by bazzer on 2007-07-27
Ok, eventually I found it myself. You need to explicity state no language support;
```
d-i pkgsel/install-language-support boolean false
```
but I'm not overjoyed by it, it seems a little contrived for my liking. Don't get me wrong, I like openoffice.org, it's a hell of a project and I use it every day. But it is not Ubuntu, and therefore I should be able to choose to install it, not have to choose NOT to install it.

---

