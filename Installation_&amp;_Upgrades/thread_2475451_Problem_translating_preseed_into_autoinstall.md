---
title: "Problem translating preseed into autoinstall"
date: 2022-05-27
forum: Installation &amp; Upgrades
---

### Post by ctnewcastle on 2022-05-27
Hi there,

I am just getting my head around the new autoinstall for deployment of ubuntu 22 (in particular how to achieve with the yaml file what I used to do with preseed)

Is there any clever people out there who can translate this old preseed file to the YAML standard required buy Ubiquity for autoinstall? Im really struggling!

d-i auto-install/enable boolean true
d-i debconf/priority select critical


d-i debian-installer/locale string en_GB.UTF-8
d-i localechooser/supported-locales multiselect en_GB.UTF-8
d-i console-setup/ask_detect boolean false
d-i keyboard-configuration/xkb-keymap select GB


### Network configuration
d-i netcfg/choose_interface select auto
d-i netcfg/link_wait_timeout string 20
d-i netcfg/dhcp_timeout string 100
d-i netcfg/get_hostname string unassigned-hostname
d-i netcfg/get_domain string unassigned-domain




### Mirror settings
d-i mirror/country string manual
d-i mirror/http/hostname string archive.ubuntu.com
d-i mirror/http/directory string /ubuntu
d-i mirror/http/proxy string


### Account setup
#d-i passwd/root-login boolean true
#d-i passwd/root-password-crypted password !!
#d-i passwd/make-user boolean false


d-i passwd/user-fullname string Student
d-i passwd/username string student
d-i passwd/user-password password (removed)
d-i passwd/user-password-again password (removed)
d-i user-setup/allow-password-weak boolean true
d-i user-setup/encrypt-home boolean false


# The root password is disabled by default. 


### Clock and time zone setup
d-i clock-setup/utc boolean true
d-i time/zone string Europe/London
d-i clock-setup/ntp boolean true


# NTP Settings 
d-i clock-setup/ntp-server string 0.uk.pool.ntp.org


### Partitioning


d-i partman-auto/init_automatically_partition select biggest_free
d-i partman-partitioning/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true
d-i partman-auto/confirm boolean true


### EFI
d-i partman-efi/non_efi_system boolean true


### Grub
d-i grub-installer/with_other_os boolean true
d-i grub-installer/bootdev string default
       
### Base system installation
d-i base-installer/install-recommends boolean true
d-i base-installer/kernel/image string linux-generic
d-i debconf debconf/frontend select Noninteractive


### Apt setup
d-i apt-setup/restricted boolean true
d-i apt-setup/universe boolean true
d-i apt-setup/backports boolean true
d-i apt-setup/use_mirror boolean false
d-i apt-setup/services-select multiselect security, updates
d-i apt-setup/security_host string security.ubuntu.com
d-i apt-setup/security_path string /ubuntu


tasksel tasksel/first multiselect server, openssh-server
tasksel tasksel/first multiselect ubuntu-desktop


d-i pkgsel/update-policy select none


d-i preseed/late_command string \


in-target wget [ftp://192.168.100.252/conf/PostInstall2004.sh](ftp://192.168.100.252/conf/PostInstall2004.sh) -O /usr/local/bin/PostInstall.sh; \
in-target chmod 777 /usr/local/bin/PostInstall.sh; \
in-target /bin/bash /usr/local/bin/PostInstall.sh


	
d-i debian-installer/splash boolean false


d-i finish-install/reboot_in_progress note

---

