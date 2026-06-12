---
title: "Preseed not loading"
date: 2012-08-07
forum: Installation &amp; Upgrades
---

### Post by rockskull on 2012-08-07
Hi there. 

I made a USB stick with ubuntu server 10.04 x86 iso using unetbootin.

I have modified the syslinux.cfg to read my preseed file, but it seems it's not. I know I'm modifiying the right file, because i was able to see changes in the menu entries. 

the file is in the /preseed directory. When I choose the default option (wich is the one modified) the installer asks me for a lot of configured stuff n the preseed file.

syslinux.cfg looks like this:

```

default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/preseed.seed quiet --
```

My preseed.seed file:

```

############## LANGUAGE & LOCALE #################
# Locale sets language and country.
d-i debian-installer/locale string pt_BR
# Keyboard selection.
# Disable automatic (interactive) keymap detection.
d-i console-setup/ask_detect boolean false
d-i console-setup/layoutcode string br
d-i console-setup/modelcode string abnt2
#Clock Configuration
#Enable UTC
d-i clock-setup/utc boolean true
#Timezone
d-i time/zone string America/Sao_Paulo
############# NETWORK CONFIGURATION ###############
#Choose ethernet interface
d-i netcfg/choose_interface select eth0
#Disable DHCP
d-i netcfg/disable_dhcp boolean true
# Static network configuration.
d-i netcfg/get_nameservers string 192.168.1.1
d-i netcfg/get_ipaddress string 192.168.1.35
d-i netcfg/get_netmask string 255.255.255.0
d-i netcfg/get_gateway string 192.168.1.1
d-i netcfg/confirm_static boolean true
#Hostname (Change after installation)
d-i netcfg/get_hostname string SERVER
#Domain
d-i netcfg/get_domain string NETWORK
# Disable that annoying WEP key dialog.
d-i netcfg/wireless_wep string
############ REPOSITORY ##############
### Mirror settings
# If you select ftp, the mirror/country string does not need to be set.
#d-i mirror/protocol string http
#d-i mirror/country string manual
#d-i mirror/http/hostname string 192.168.1.236
#d-i mirror/http/directory string /ubuntu
d-i mirror/http/proxy string http://user:123456@192.168.1.1:3128
################### PARTITIONING ####################
#Set wich disk should be used
d-i partman-auto/disk string /dev/sda
#Set the method to regular (could also be crypto or lvm)
d-i partman-auto/method string regular
#This line describes how the disk should be partitioned and formatted
#d-i partman-auto/expert_recipe string boot-root :: 30053 50 30053 ext4\
d-i partman-auto/expert_recipe string boot-root :: 6000 50 6000 ext4\
	$primary{ } $bootable{ } \
	mehotd{ format } format{ } \
	use_filesystem{ } filesystem{ ext4 } \
	mountpoint{ / }	.
#Ignores the question about not having a swap
d-i partman-basicfilesystems/no_swap boolean false
d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true
#Install the linux generic kernel
d-i base-installer/kernel/image string linux-generic
################# Users & Accounts  ##################
#Define root password
d-i passwd/root-password password r00tpa$$wd
d-i passwd/root-password-again password r00tpa$$wd
#Create User
d-i passwd/user-fullname string MyUser
d-i passwd/username string theuser
d-i passwd/user-password password 123456
d-i passwd/user-password-again password 123456
#Perimitir senha fraca
d-i user-setup/allow-password-weak boolean true
############## APT Configuration #############
d-i apt-setup/restricted boolean true
d-i apt-setup/universe boolean true
d-i apt-setup/backports boolean true
############ PACKGES ###############
tasksel tasksel/first multiselect standard
#Install openshh-server
d-i pkgsel/include string openssh-server build-essential
#Disable package upgrade
d-i pkgsel/upgrade select none
#No automatic updates
d-i pkgsel/update-policy select none
#Do not send back information
popularity-contest popularity-contest/participate boolean false
################# Boot Loader #################
#Only debian will be installed, so put grub in the MBR
d-i grub-installer/only_debian boolean true
########## FINISHING UP ##########
#Don't show finished message
d-i grub-installer/only_debian boolean true

```

---

### Post by rockskull on 2012-08-07
One more info, I got this same pattern either using linux usb creator and unetbootin

---

