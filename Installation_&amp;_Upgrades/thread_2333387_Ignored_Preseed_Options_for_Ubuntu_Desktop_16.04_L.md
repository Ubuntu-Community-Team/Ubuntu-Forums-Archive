---
title: "Ignored Preseed Options for Ubuntu Desktop 16.04 LTS"
date: 2016-08-09
forum: Installation &amp; Upgrades
---

### Post by histamineblkr on 2016-08-09
Issue

I have accomplished a completely unattended install of Ubuntu 16.04.1 LTS. It is very simple and rather generic, but I can put the CDROM in and walk away. The current issue is with installing packages and using either the ubiquity/success_command and the d-i preseed/late_command string ... 
It seems, all of these are ignored.
According to Ubiquity documentation the following are ignored, found [here]("https://wiki.ubuntu.com/UbiquityAutomation"):
[LIST]
[*]netcfg 
[*]LVM and RAID partitioning 
[*]base-installer 
[*]pkgsel/tasksel 
[*]finish-install 
[/LIST]
So using something like
```
d-i pkgsel/include string openssh-server salt-minion vim wget
```
has no effect at all.

I have researched for a few days now and common suggestions are to use the preseed/early_command or preseed/late_command. I have tried many different ways to get this to work, but none have so far. The Ubuntu documentation found [here]("https://help.ubuntu.com/16.04/installation-guide/example-preseed.txt") suggests to write in:
```
d-i preseed/late_command string apt-install zsh
```
produces no result. 

After looking at the syntax, I though 'apt-install' looks syntacticly weird so maybe this would work:
```
d-i preseed/late_command string in-target /usr/bin/apt-get install zsh
```
still it produced nothing.

I have also tried using the package 'system-config-kickstart' to create a kickstart file that would just install the packages I desire, but I have been unable to get that to work either. I will continue trying various kickstart files to see if I can get it to work, but it seems you have to include a lot of redundant options. I'm not sure how many option I can comment out, can I leave only the package part in and use just that portion for a kickstart file? According to the source code found [here]("http://bazaar.launchpad.net/~ubuntu-installer/kickseed/master/files/head:/handlers/"), it hasn't been updated much with the most recent being 2014, but most around 2009. Also, no script to handle packages so I think that maybe a kickstart will not be much of an option. 

Any help as to why the Ubuntu installer/Ubiquity or the preseed file is ignoring those options would be greatly appreciated.

Current preseed file (I took out the encrypted passwords and usernames):
```

# Partitioning
d-i partman-auto/disk string /dev/sda
d-i partman-auto/method string regular
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-md/device_remove_md boolean true
d-i partman-auto/choose_recipe select atomic

# This makes partman automatically partition without confirmation
d-i partman-partitioning/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true

# Locale
d-i debian-installer/locale string en_US
d-i console-setup/ask_detect boolean false
d-i console-setup/layoutcode string us

# Network
d-i netcfg/get_hostname string unassigned-hostname
d-i netcfg/get_domain string unassigned-domain
d-i netcfg/choose_interface select auto

# Clock 
d-i clock-setup/utc-auto boolean true
d-i clock-setup/utc boolean true
d-i time/zone string US/Pacific
d-i clock-setup/ntp boolean true

# Packages, Mirrors, Image
d-i base-installer/kernel/override-image string linux-image-amd64
d-i mirror/country string US
d-i mirror/http/proxy string
d-i apt-setup/restricted boolean true
d-i apt-setup/universe boolean true
#d-i pkgsel/install-language-support boolean false
#tasksel tasksel/first multiselect ubuntu-desktop
#d-i pkgsel/include string openssh-server salt-minion vim wget
#d-i pkgsel/upgrade full-upgrade

# Users
d-i passwd/user-fullname string <User Name>
d-i passwd/username string <user>
d-i passwd/user-password-crypted password <crypt 3 passwd>
d-i passwd/user-default-groups string adm audio cdrom dip lpadmin sudo plugdev sambashare video
d-i passwd/root-login boolean true
d-i passwd/root-password-crypted password <crypt 3 passwd>
d-i user-setup/allow-password-weak boolean true

# Grub
d-i grub-installer/grub2_instead_of_grub_legacy boolean true
d-i grub-installer/only_debian boolean true
d-i finish-install/reboot_in_progress note

# Custom Commands
d-i preseed/late_command string apt-install salt-minion

```

Current boot parameters in isolinux/isolinux.cfg:
```

default live-install
label live-install
  menu label ^Install Ubuntu
  kernel /casper/vmlinuz.efi
  append  file=/cdrom/ks.preseed auto=true priority=critical debian-installer/locale=en_US keyboard-configuration/layoutcode=us ubiquity/reboot=true languagechooser/language-name=English countrychooser/shortlist=US localechooser/supported-locales=en_US.UTF-8 boot=casper automatic-ubiquity initrd=/casper/initrd.lz quiet splash noprompt noshell ---

```

---

