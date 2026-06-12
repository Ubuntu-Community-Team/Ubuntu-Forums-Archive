---
title: "grub install problems with custom install kit"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by roblem on 2010-04-09
I'm developing a custom install distro for a project so that all boxes are installed the same way. So far, this has been a piece of cake, and its installed on a lot of platforms very nicely.

However, I got a new x86 box that has SATA RAID.  The usual Ubuntu install installs just fine, but my custom install fails to perform the grub install.   It complains that grub-install has asked to be left unconfigured.  I've tried (hd0,0) and (sd0,0) as targets.  The usual Ubuntu install uses (hd0,0).

Here is my preseed file (less important stuff removed for brevity).  Any hints at all?

d-i debian-installer/locale string en_US
d-i console-setup/ask_detect boolean false
d-i console-setup/layoutcode string us
#
#
d-i netcfg/disable_dhcp boolean true
d-i netcfg/choose_interface select eth0
d-i netcfg/dhcp_options select Configure network manually
d-i netcfg/get_hostname string foo
d-i netcfg/get_domain string foo.net
d-i netcfg/wireless_wep string

d-i hw-detect/load_firmware boolean true
d-i mirror/http/proxy string
d-i clock-setup/utc boolean false
d-i time/zone string GMT
d-i clock-setup/ntp boolean true
d-i partman-auto/method string lvm
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-lvm/confirm boolean true
d-i partman-auto-lvm/guided_size string max
d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true

d-i passwd/root-password-crypted password xxxx

d-i passwd/user-fullname string Foo account
d-i passwd/username string foo
d-i passwd/user-password-crypted password xxxx
d-i passwd/auto-login boolean false

d-i user-setup/allow-password-weak boolean true
d-i user-setup/encrypt-home boolean false

tasksel tasksel/first multiselect minimal

d-i pkgsel/include string \
    acpi-support \
    alacarte 
.
.
.

d-i debian-installer/allow_unauthenticated string true
d-i pkgsel/upgrade select none
d-i pkgsel/update-policy select none
d-i grub-installer/bootdev  string (hd0,0)
d-i grub-installer/only_debian boolean true
d-i grub-installer/password password 123456
d-i grub-installer/password-again password 123456
d-i finish-install/reboot_in_progress note

xserver-xorg xserver-xorg/autodetect_monitor boolean true

---

