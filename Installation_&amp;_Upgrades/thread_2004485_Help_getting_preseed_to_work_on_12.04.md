---
title: "Help getting preseed to work on 12.04?"
date: 2012-06-15
forum: Installation &amp; Upgrades
---

### Post by maniacbug on 2012-06-15
Hi, I am having a bit of trouble getting a pre-seed to work completely in 12.04.  Wondering if anyone could help point me on the right track.

My goal is a 12.04 64-bit desktop installation with zero user prompts beyond the initial isolinux menu.

What I did: 
 
[LIST=1]
[*] Downloaded [http://releases.ubuntu.com/12.04/ubuntu-12.04-desktop-amd64.iso](http://releases.ubuntu.com/12.04/ubuntu-12.04-desktop-amd64.iso)
[*] Edited the iso using isomaster
[*] Added the attached preseed file to /preseed/
[*] Edited isolinux/txt.cfg as attached
[*] Edited isolinux/isolinux.cfg as attached
[*] Launched VirtualBox using 12.04 64-bit Ubuntu as host OS, with this ISO assigned as the CD
[*]Picked the new 'Maniac System 4' from the boot menu.
[/LIST]
 What I wanted to have happen: 
 
[LIST=1]
[*] Install complete desktop system with no user prompts whatsoever
[/LIST]
 What happened instead:  Several screens come up. 
 
[LIST]
[*] "Welcome", asking for language.
[*] "Preparing to install Ubuntu"
[*] "Installation type"  The partition settings are just fine.  Uses almost all the available disk, partitions a little for swap.
[*] "Where are you?"
[*] "Keyboard layout"
[*] "Who are you?"  Note that it does pick up the fullname,  username, and host name correctly from the preseed file!  Doesn't pick  up the password.
[/LIST]

---

### Post by flipybcn on 2013-03-11
Any luck with the preseeding installation?

---

### Post by flipybcn on 2013-04-04
I managed to make a preseeding installation, some steps (as asking for a hostname or showing the debian installer in a specific language or installing a subset of languages) are still failing.

Using alternate LTS CD.

preseed.cfg:
```
d-i debian-installer/language string en_US
d-i debian-installer/country string ES
d-i debian-installer/locale string en_US.UTF-8

d-i localechooser/supported-locales en_US.UTF-8, es_ES.UTF-8, ca_ES.UTF-8
d-i localechooser/languagelist en_US, es_ES, ca_ES

d-i console-setup/ask_detect boolean false
d-i keyboard-configuration/layoutcode string es
d-i console-keymaps-at/keymap select sg-latin1

d-i netcfg/choose_interface select auto
#d-i netcfg/get_hostname string ubuntu-machine
d-i netcfg/get_hostname seen false
d-i netcfg/get_domain string domain.ltd
d-i netcfg/wireless_wep string

d-i hw-detect/load_firmware boolean true

d-i clock-setup/utc boolean true
d-i time/zone string Europe/Madrid
d-i clock-setup/ntp boolean true
d-i clock-setup/ntp-server string 192.168.0.1

d-i partman-auto/disk string /dev/sda
d-i partman-auto/method string lvm
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-md/device_remove_md boolean true
d-i partman-lvm/confirm boolean true
#d-i partman-auto/choose_recipe select home
d-i partman-auto/choose_recipe select atomic
d-i partman/default_filesystem string ext4
d-i partman-partitioning/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true
d-i partman/mount_style select uuid

d-i passwd/user-fullname string myuser
d-i passwd/username string myuser
d-i passwd/user-password-crypted password $1$CfLT.WmM$DnxygmZUjOKv6LrMtXWup1
d-i user-setup/allow-password-weak boolean false

d-i mirror/country string manual
d-i mirror/http/hostname string my.repo.com
d-i mirror/http/directory string /ubuntu
d-i mirror/suite string precise
d-i mirror/udeb/components multiselect main, restricted, multiverse, universe

d-i apt-setup/restricted boolean true
d-i apt-setup/universe boolean true
d-i apt-setup/multiverse boolean true
d-i apt-setup/services-select multiselect security 
d-i apt-setup/security_host string my.repo.com
d-i apt-setup/security_path string /ubuntu
#d-i debian-installer/allow_unauthenticated boolean true

tasksel tasksel/first multiselect ubuntu-desktop
#tasksel tasksel/first multiselect kubuntu-desktop
d-i pkgsel/include string openssh-server likewise-open-gui subversion
d-i pkgsel/upgrade select full-upgrade
d-i pkgsel/language-packs multiselect en_US, es_ES, ca_ES
d-i pkgsel/update-policy select none
d-i pkgsel/updatedb boolean true
d-i grub-installer/only_debian boolean true
#d-i grub-installer/with_other_os boolean true
#d-i finish-install/reboot_in_progress note
d-i preseed/late_command string \
	echo "greeter-hide-users=true" >> /target/etc/lightdm/lightdm.conf; \
	in-target apt-get remove -y libnss-mdns; \
	in-target add-apt-repository ppa:webupd8team/java; \
	in-target apt-get -y update

xserver-xorg xserver-xorg/autodetect_monitor boolean true
xserver-xorg xserver-xorg/config/monitor/lcd boolean true
xserver-xorg xserver-xorg/config/monitor/selection-method \
       select medium
xserver-xorg xserver-xorg/config/monitor/mode-list \
       select 1024x768 @ 60 Hz
```

isolinux.cfg:
```
prompt 0
timeout 1
default install
label install
  menu label ^Install Ubuntu
  kernel /install/vmlinuz
  append file=/cdrom/preseed/preseed.cfg ipv6.disable=1 debian-installer=en_US locale=es_ES fb=false debconf/frontend=noninteractive console-setup/ask_detect=false console-setup/layoutcode=es kbd-chooser/method=es console-keymaps-at/keymap=es priority=critical initrd=/install/initrd.gz splash quiet --
```

---

