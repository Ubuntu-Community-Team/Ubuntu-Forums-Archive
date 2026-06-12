---
title: "Failed to run preseeded command"
date: 2016-12-30
forum: Installation &amp; Upgrades
---

### Post by pravink on 2016-12-30
Hi am getting an error during automated installation for late_command. "Execution of preseeded command failed with error code 1.

Below is my preseed file output.

d-i auto-install/enable boolean true
d-i debconf/priority string critical
d-i pkgsel/update-policy select none
# Localization
d-i debian-installer/language string en
d-i debian-installer/country string US
d-i debian-installer/locale string en_US.UTF-8
d-i localechooser/supported-locales multiselect en_US.UTF-8
# Keyboard selection.
# Disable automatic (interactive) keymap detection.
d-i console-setup/ask_detect boolean false
d-i keyboard-configuration/xkb-keymap select us
d-i netcfg/choose_interface select auto
d-i netcfg/dhcp_timeout string 60
d-i netcfg/get_hostname string unassigned-hostname
d-i netcfg/get_domain string unassigned-domain
d-i netcfg/wireless_wep string
d-i clock-setup/utc boolean true
d-i partman-auto/init_automatically_partition select biggest_free
d-i pkgsel/upgrade select none
#d-i finish-install/reboot_in_progress note
d-i pkgsel/include string openssh-server build-essential xorg icewm
# Users
d-i passwd/user-fullname string kiosk
d-i passwd/username string kiosk
d-i passwd/user-password-crypted 123456 [crpyt 3]
d-i passwd/root-login boolean true
d-i passwd/root-password-crypted 123456 [crypt 3]
d-i user-setup/allow-password-weak boolean tru
d-i preseed/late_command string /bin/echo "startx">>/target/home/kiosk/.profile 
in-target mkdir -pv /etc/systemd/system/getty@tty1.service.d; 
in-target echo "[Service]" >> /etc/systemd/system/getty@tty1.service.d/autologin.conf; 
in-target echo "ExecStart=" >> /etc/systemd/system/getty@tty1.service.d/autologin.conf; 
in-target echo "ExecStart=-/sbin/agetty --autologin kiosk --noclear %I 38400 linux" >> /etc/systemd/system/getty@tty1.service.d/autologin.conf
d-i preseed/late_command string cp -a /cdrom/preseed/post-install.sh /target/post-install.sh; in-target /bin/bash /post-install.sh
d-i finish-install/reboot_in_progress note

---

