---
title: "Network Install 18.04 bionic via preseed"
date: 2019-03-20
forum: Installation &amp; Upgrades
---

### Post by foerni02 on 2019-03-20
Hello 

I am new to this forum.  I am an administrator from Germany. At the moment I have problem with the automated network deployment of Ubuntu Bionic. 

I tried (for at least 2 weeks.. ) to bulid a startable Install iso. I have set up an apache server with loop mounted iso´s of Ubuntu 16.04 and 18.04.2. A Network internal ubuntu mirror is also in place and working.

the deployment of ubuntu 16.04 is working fine. I have NO INTERNET connection in this environment.

As have figured out my problem is the initrd.gz and the linux file in the iso image. 

Is someone able to tell me which files i have to take and where to find them ? - I also tried to use the netboot files in the mini.iso with no success. 

THX

start.iso :
[PHP]
txt.cfg 

default install
label install
    menu label ^Install
    menu default
    kernel linux
    append vga=788 initrd=initrd.gz --- quiet 
label cli
    menu label ^Command-line install
    kernel linux
    append tasks=standard pkgsel/language-pack-patterns= pkgsel/install-language-support=false vga=788 initrd=initrd.gz --- quiet 


label install 
    menu label ^Install Ubuntu 16_04 LTS
    menu default
    kernel /kernel/ubuntu_16/x86_64/linux auto=true preseed/url=http://XXX.XXX.XXX.XXX/preseeds/ubuntu-server.cfg netcfg/disable_dhcp=true netcfg/get_ipaddress=XXX.XXX.XXX.XXX netcfg/get_gateway=XXX.XXX.XXX.XXX netcfg/get_nameservers=XXX.XXX.XXX.XXX netcfg/get_netmask=XXX.XXX.XXX.XXX
    append vga=788 initrd=/kernel/ubuntu_16/x86_64/initrd.gz --- quiet live-installer/net-image=http://XXX.XXX.XXX.XXX/ubuntu/xenial/install/filesystem.sqaushfs


label install 
    menu label ^Install Ubuntu 18_04 LTS
    menu default
    kernel /kernel/ubuntu_18/amd64/linux automated-ubiquity auto=true preseed/url=http://XXX.XXX.XXX.XXX/preseeds/ubuntu-server-18.cfg netcfg/disable_dhcp=true netcfg/get_ipaddress=XXX.XXX.XXX.XXX netcfg/get_gateway=XXX.XXX.XXX.XXX netcfg/get_nameservers=XXX.XXX.XXX.XXX netcfg/get_netmask=XXX.XXX.XXX.XXX
    append vga=788 initrd=/kernel/ubuntu_18/amd64/initrd.gz --- quiet live-installer/net-image=http://XXX.XXX.XXX.XXX/ubuntu/bionic/install/filesystem.sqaushfs 

[/PHP]

The preseed file is downloaded by the Installer.

[PHP]d-i debian-installer/locale string en_US
d-i keymap select de
d-i console-setup/ask_detect boolean false
d-i keyboard-configuration/xkb-keymap select de
d-i keyboard-configuration/layoutcode string de

# Static network configuration.
d-i netcfg/choose_interface select auto
d-i netcfg/disable_autoconfig boolean true
d-i netcfg/dhcp_failed note
d-i netcfg/dhcp_options Configure network manually
d-i netcfg/get_ipaddress string XXX.XXX.XXX
d-i netcfg/get_netmask string XXX.XXX.XXX
d-i netcfg/get_gateway string XXX.XXX.XXX
d-i netcfg/get_nameservers string XXX.XXX.XXX
d-i netcfg/confirm_static boolean true
d-i netcfg/get_hostname string ubuntu
d-i netcfg/get_domain string XXXX.XXX
d-i netcfg/wireless_wep string

### Mirror settings
d-i mirror/country string manual
d-i mirror/http/hostname string XXXX.XXX.de 
d-i mirror/http/directory string /ubuntu/bionic

# Suite to install.
d-i mirror/suite string bionic 

# To create a normal user account.
d-i passwd/user-fullname string user
d-i passwd/username string user 
d-i passwd/user-password-crypted password XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX 

# Set to true if you want to encrypt the first user's home directory.
d-i user-setup/encrypt-home boolean false


### Clock and time zone setup
d-i clock-setup/utc boolean true
d-i time/zone string Europe/Berlin
d-i clock-setup/ntp boolean true

# NTP server  
d-i clock-setup/ntp-server string XXX.XXX.XXX.de

# HDD Setup
d-i partman-auto/disk string /dev/sda
d-i partman-auto/method string lvm
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-md/device_remove_md boolean true
d-i partman-lvm/confirm boolean true
d-i partman-lvm/confirm_nooverwrite boolean true
d-i partman-partitioning/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true
d-i partman-auto/expert_recipe string                         \
      boot-root ::                                            \
              300 300 300 ext2                                \
                      $primary{ } $bootable{ }                \
                      method{ format } format{ }              \
                      use_filesystem{ } filesystem{ ext2 }    \
                      mountpoint{ /boot }                     \
              .                                               \
              100% 4098 100% linux-swap                       \
                      lv_name{ swap }                         \
                      method{ swap } format{ }                \
                      $lvmok{ }                               \
              .                                               \
              10240 10240 10240 ext3                          \
                      lv_name{ root }                         \
                      method{ lvm } format{ }                 \
                      use_filesystem{ } filesystem{ ext3 }    \
                      mountpoint{ / }                         \
                      $lvmok{ }                               \
              .                                               \
              10240 10240 10240 xfs                           \
                      lv_name{ home }                         \
                      method{ lvm } format{ }                 \
                      use_filesystem{ } filesystem{ ext3 }     \
                      mountpoint{ /home }                     \
                      $lvmok{ }                               \
              .                                               \
              20480 20480 20480 xfs                           \
                      lv_name{ var }                          \
                      method{ lvm } format{ }                 \
                      use_filesystem{ } filesystem{ xfs }     \
                      mountpoint{ /var }                      \
                      $lvmok{ }                               \
              .                                               \

d-i partman-md/confirm boolean true
d-i partman-partitioning/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true


d-i apt-setup/use_mirror boolean true 
d-i apt-setup/backports boolean false
d-i apt-setup/update boolean true 
d-i apt-setup/services-select multiselect security
d-i apt-setup/security_host string XXX.XXX.XXX 
d-i apt-setup/security_path string /ubuntu-security
d-i apt-setup/hostname string XXX.XXX.XXX
d-i apt-setup/directory string /ubuntu

### Package selection
tasksel tasksel/first multiselect standard 

# Individual additional packages to install

d-i pkgsel/include string openssh-server build-essential open-vm-tools xinetd btrfs-tools  

# Language pack selection
d-i pkgsel/language-packs multiselect de, en
d-i pkgsel/update-policy select none 


# GRUB Install

d-i grub-installer/grub2_instead_of_grub_legacy boolean true
d-i grub-installer/only_debian boolean true
d-i grub-installer/with_other_os boolean true
d-i grub-installer/bootdev string /dev/sda
d-i finish-install/reboot_in_progress note

d-i preseed/run string http://XXX.XXX.de/scripte/preseed.sh

# post install script
d-i preseed/late_command string \
      cd /target; \
        wget http://XXX.XXX.de/files/sources.list; \
    in-target cp sources.list /etc/apt/ ;\
    in-target rm -rf /var/lib/apt/lists ; \
      in-target apt-get update ; \
      in-target apt-get -y upgrade ; \
    in-target apt-get -y autoremove ; \
    in-target apt-get autoclean ; \
    in-target apt-get clean ; \
    cd /target; \
    wget http://XXX.XXX.de/scripte/gnome-post-install.sh; \
    chmod +x ./gnome-post-install.sh; \
    chroot ./ ./gnome-post-install.sh; \
    rm -f ./gnome-post-install.sh
    in-target echo -e "o\nn\np\n1\n\n\nw" | fdisk /dev/sdb ; \
    in-target mkfs.btrfs -m single -L "data" /dev/sdb1 -f ; \
[/PHP]

---

