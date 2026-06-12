---
title: "Proseed.cfg mirror setting didn't work"
date: 2011-04-13
forum: Installation &amp; Upgrades
---

### Post by richard_wu0313 on 2011-04-13
hi all,
i want to install ubuntu10.10 x64 by pxe, so i have following proseed.cfg. and system should install using mirror 10.1.1.2/ubuntu/ubuntu10.10/x64 according to preseed.cfg. But it always report "Bad archive mirror". i could ping 10.1.1.2 and could get file by "wget" from 10.1.1.2. any suggestion would be appreciated. thanks.

# Locale sets language and country.
d-i debian-installer/locale string en_us

# Keyboard selection.
d-i console-setup/ask_detect boolean false
d-i console-setup/layoutcode string us

# Network configuration.
d-i netcfg/choose_interface select auto
d-i netcfg/get_hostname string unassigned-hostname
d-i netcfg/get_domain string unassigned-domain

[COLOR="Red"]# Mirror settings
d-i mirror/protocol string http
d-i mirror/http/hostname string 10.1.1.2
d-i mirror/http/directory string /ubuntu/ubuntu10.10/x64
d-i mirror/http/proxy string[/COLOR]

# Clock and time zone setup
d-i clock-setup/utc boolean false
d-i time/zone string Asia/Shanghai

# Partitioning
d-i partman-auto/method string lvm
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-md/device_remove_md boolean true
d-i partman-lvm/confirm boolean true
d-i partman-auto-lvm/guided_size string max
d-i partman-auto/choose_recipe select atomic
d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true

# Base system installation
d-i base-installer/kernel/image string linux-generic

# Account setup
d-i passwd/root-login boolean true
d-i passwd/root-password password 123456
d-i passwd/root-password-again password 123456
d-i passwd/make-user boolean false
d-i user-setup/encrypt-home boolean false

# Package selection
tasksel tasksel/first multiselect standard
d-i pkgsel/include string openssh-server
d-i pkgsel/upgrade select none
d-i pkgsel/language-packs multiselect en, zh
d-i pkgsel/update-policy select none

# Boot loader installation
d-i grub-installer/only_debian boolean true

# Finishing up the installation
d-i finish-install/reboot_in_progress note

---

### Post by richard_wu0313 on 2011-04-19
after investigation. preseed.cfg should be used like this "append preseed/url=http://....." if you are using http protocal
and following config should also be added in preseed.

Here is the code for install mirror.
# If you choose ftp or http, you'll be asked for a country and a mirror.
base-config apt-setup/country select enter information manually
base-config apt-setup/hostname string xx.xx.xx.xx
base-config apt-setup/directory string /ubuntu
# Stop after choosing one mirror.
base-config apt-setup/another boolean false

---

