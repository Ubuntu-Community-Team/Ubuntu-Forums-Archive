---
title: "Netbooting 6.10 woes :("
date: 2006-11-29
forum: Installation &amp; Upgrades
---

### Post by bobg on 2006-11-29
Hi guys,
I'm fairly new to ubuntu and had a few questions, my answers don't seem to have been answered in this forum elsewhere so I was hoping someone may be able to help.

I am trying to piece together a imaging system which will allow my to format and re-install ubuntu on clients. The idea is I want to connect to a server, download a preseed file, install whatever packages need to be installed on the the client(either from the unbuntu website or my proxy if the files already cached), then run some commands just before install. I thought ubuntu wold be perfect for this with its preseeding commands. 

I am at the point where I can get the following going:

PXE boot off a client
get an IP via a DHCP server
copy down the netboot install files via TFTP
The installation goes through, most of it is sucessfully automated through my preseed script which lives on the server. However I have 2 major problems at the end of my install.

1) I have no GUI. Gnome is not installed, at least as far as I can tell. and I have no reason why. I have tried this on three different client with totally different hardware and got the same results.

2) my keyboard isn't configured properly and what is even more scary is if I go to the "configure keyboard" option during the install. It won't open, it just jumps to whatever it was up to next :s.

I have attached a copy of my preseed file.(I've removed my machines IP's etc...etc...)


-------------------------START----------------------------------

d-i debian-installer/locale string en_US
d-i console-keymaps-at/keymap select us
d-i console-setup/variant	select	U.S. English
d-i console-setup/compose	select	No compose key
d-i console-setup/fontsize-text	select	16
d-i netcfg/choose_interface select auto
d-i netcfg/get_hostname string myhost 
d-i netcfg/get_domain string foo.bar
d-i netcfg/wireless_wep string
d-i mirror/country string enter information manually
d-i mirror/http/hostname string archive.ubuntu.com
d-i mirror/http/directory string /ubuntu
d-i mirror/suite string edgy 
d-i mirror/http/proxy string [http://myproxy/](http://myproxy/)
d-i partman-auto/disk string /dev/discs/disc0/disc
d-i partman-auto/method string lvm
d-i partman-auto/purge_lvm_from_device boolean true
d-i partman-lvm/confirm boolean true
d-i partman-auto/choose_recipe \
       select All files in one partition (recommended for new users)
d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition \
       select Finish partitioning and write changes to disk
d-i partman/confirm boolean true
d-i clock-setup/utc boolean true
d-i time/zone string US/Eastern
base-config  apt-setup/uri_type         select http
d-i  apt-setup/country          select enter information manually
d-i  apt-setup/hostname         string archive.ubuntu.com
d-i  apt-setup/directory        string /ubuntu
d-i  apt-setup/another          boolean false
d-i passwd/user-fullname string user User
d-i passwd/username string testuser
d-i passwd/user-password password testpass
d-i passwd/user-password-again password testpass
d-i grub-installer/only_debian boolean true
d-i grub-installer/with_other_os boolean true
tasksel tasksel/first multiselect ubuntu-desktop 
d-i pkgsel/install-pattern string ~^tubuntu-standard|~n^ubuntu-desktop
d-i finish-install/reboot_in_progress note
exim4-config exim4/dc_eximconfig_configtype \
       select no configuration at this time
exim4-config exim4/no_config boolean true
exim4-config exim4/no_config boolean true
exim4-config exim4/dc_postmaster string
xserver-xorg xserver-xorg/config/device/driver select vesa
xserver-xorg xserver-xorg/autodetect_monitor boolean true
xserver-xorg xserver-xorg/config/monitor/lcd boolean true
xserver-xorg xserver-xorg/config/monitor/selection-method \
       select medium
xserver-xorg xserver-xorg/config/monitor/mode-list \
       select 1024x768 @ 60 Hz
gdm     shared/default-x-display-manager        select gdm

---------------------END--------------------------------

---

