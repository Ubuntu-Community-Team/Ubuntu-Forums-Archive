---
title: "Installing 14.04 Seed Netowrk install EFI + Raid1 + LVM, How to do EFI?"
date: 2014-07-15
forum: Installation &amp; Upgrades
---

### Post by nameending on 2014-07-15
Hello,

Trying to do a setup of some servers, and they all have UEFI options, and I'd like to install (Via Seed file) to the EFI partition.  Can't seem to figure out how though.  I can create legit Fat32 partitions that are 256meg in size for UEFI to use, but I'm not sure in the seed file syntax how to make these partitions UEFI-able via Seed file only.  I've attached a portion of my seed file below for perusal.

Thanks in Advance.


```

# Mostly based on the Ubuntu installation guide
# https://help.ubuntu.com/12.04/installation-guide/


# Preseeding only locale sets language, country and locale.
d-i debian-installer/locale string en_US


# Keyboard selection.
# Disable automatic (interactive) keymap detection.
d-i console-setup/ask_detect boolean false
d-i keyboard-configuration/layoutcode string us
d-i keyboard-configuration/variantcode string


# netcfg will choose an interface that has link if possible. This makes it
# skip displaying a list if there is more than one interface.
#set $myhostname = $getVar('hostname',$getVar('name','cobbler')).replace("_","-")
d-i netcfg/choose_interface select auto
d-i netcfg/get_hostname string $myhostname


# If non-free firmware is needed for the network or other hardware, you can
# configure the installer to always try to load it, without prompting. Or
# change to false to disable asking.
# d-i hw-detect/load_firmware boolean true


# NTP/Time Setup
d-i time/zone string US/Eastern
d-i clock-setup/utc boolean true
d-i clock-setup/ntp boolean true
d-i clock-setup/ntp-server  string ntp.ubuntu.com


# Setup the installation source
d-i mirror/protocol string http
d-i mirror/country string manual
d-i mirror/http/hostname string us.archive.ubuntu.com
d-i mirror/http/directory string /ubuntu
d-i mirror/http/proxy string


#set $os_v = $getVar('os_version','')
#if $os_v and $os_v.lower()[0] > 'p'
# Required at least for 12.10+
d-i live-installer/net-image string http://$http_server/cobbler/links/$distro_name/install/filesystem.squashfs
#end if


# Suite to install.
d-i mirror/suite string trusty
d-i mirror/udeb/suite string trusty


# Components to use for loading installer components (optional).
#d-i mirror/udeb/components multiselect main, restricted


# Disk Partitioning
# Use LVM, and wipe out anything that already exists
d-i partman/early_command string vgs -separator=: -noheadings | cut -f1 -d: | while read vg ; do vgchange -an \$vg ; done ; pvs -separator=: -noheadings | cut -f1 -d: | while read pv ; do pvremove -ff -y \$pv ; done


d-i partman/early_command \
     string /bin/dd if=/dev/zero of=/dev/sda bs=512 count=1


d-i partman/early_command \
     string /bin/dd if=/dev/zero of=/dev/sdb bs=512 count=1


# Disk Partitioning From Tom C


d-i     partman-lvm/device_remove_lvm                 boolean true
d-i     partman-md/device_remove_md                   boolean true
d-i     partman-lvm/confirm                           boolean true
d-i     partman-auto/disk                             string /dev/sda /dev/sdb
d-i     partman-auto/method                           string raid
d-i     partman-auto-lvm/new_vg_name                  string vg0
d-i     partman-auto-lvm/guided_size                  string 90%
d-i     partman-auto/expert_recipe string \
    efi-lvm ::        \
256 10 256 fat32        \
    \$primary{ }         \
    \$lvmignore{ }       \
    method{ efi }       \
    format{ }           \
.\
    20000 30 1000000000 raid    \
    \$lvmignore{ }         \
    \$primary{ }         \
    method{ raid }        \
    .\
    20000 50 400000 ext4     \
    \$defaultignore{ }     \
    \$lvmok{ }         \
    lv_name{ root }      \
    method{ format }     \
    format{ }         \
    use_filesystem{ }     \
    filesystem{ ext4 }     \
    mountpoint{ / }     \
    label{ Root }         \
    .\
    2048 40 2048 swap     \
    \$defaultignore{ }    \
    \$lvmok{ }         \
    lv_name{ swap }        \
    method{ swap }         \
    format{ }        \
    .


d-i     partman-auto-raid/recipe string \
    1 2 0 lvm - /dev/sda2#/dev/sdb2 \
    .
d-i     partman-md/confirm                            boolean true


d-i     partman-partitioning/confirm_write_new_label  boolean true
d-i     partman/choose_partition                      select Finish partitioning and write changes to disk
d-i     partman/confirm                               boolean true
# d-i     partman-md    partman-md/confirm_nochanges    boolean    false
d-i     partman-md/confirm_nooverwrite                boolean true
d-i     partman/confirm_nooverwrite                   boolean true
d-i     mdadm/boot_degraded                boolean true




# Enable deb-src lines
# d-i apt-setup/local0/source boolean true


# URL to the public key of the local repository; you must provide a key or
# apt will complain about the unauthenticated repository and so the
# sources.list line will be left commented out
# d-i apt-setup/local0/key string http://local.server/key


# By default the installer requires that repositories be authenticated
# using a known gpg key. This setting can be used to disable that
# authentication. Warning: Insecure, not recommended.
# d-i debian-installer/allow_unauthenticated boolean true


# Individual additional packages to install
# wget is REQUIRED otherwise quite a few things won't work
# later in the build (like late-command scripts)
d-i pkgsel/include string ntp ssh wget docker.io chef ifenslave-2.6 koan kvm
chef chef/chef_server_url select https://chef-01-ewr.dyndns.com:4000


# Use the following option to add additional boot parameters for the
# installed system (if supported by the bootloader installer).
# Note: options passed to the installer will be added automatically.
d-i debian-installer/add-kernel-opts string $kernel_options_post


# Avoid that last message about the install being complete.
d-i finish-install/reboot_in_progress note


## Figure out if we're kickstarting a system or a profile
#if $getVar('system_name','') != ''
#set $what = "system"
#else
#set $what = "profile"
#end if


# This first command is run as early as possible, just after preseeding is read.
# d-i preseed/early_command string [command]
d-i preseed/early_command string wget -O- \
   http://$http_server/cblr/svc/op/script/$what/$name/?script=preseed_early_default | \
   /bin/sh -s





```

---

