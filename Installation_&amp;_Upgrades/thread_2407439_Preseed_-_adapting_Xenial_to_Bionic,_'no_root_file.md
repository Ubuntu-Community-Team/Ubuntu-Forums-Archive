---
title: "Preseed - adapting Xenial to Bionic, 'no root filesystem defined'"
date: 2018-12-04
forum: Installation &amp; Upgrades
---

### Post by rob.johnson on 2018-12-04
Hey all,

So I have a PXE deployment setup which works fine with 16.04. Now that 18.04 is out and stable, I'm adding it to my deployment options. However, the preseed I wrote for Xenial isn't working with Bionic. Seems that no matter what I do, it cannot either find the local disk or can't partition it correctly, since I always get the error 'No root filesystem defined'. It doesn't even allow me to go into the wizard and specify it manually; just an OK dialog on a loop.

The computers I'm testing with are Dell XPS 13 9370s. Like most of our other machines, they use NVMe SSDs. My Xenial preseed deploys to these without issue. The basics of the deployment are:
[LIST]
[*]Full disk encryption with a fixed initial key (end user will set their own)
[*]Uses our internal Ubuntu mirror for package installation
[*]No user accounts created, only root
[*]Grub installed
[*]Post-install script then customises the deployment to our needs - LDAP authentication, developer tools setup etc.
[/LIST]

 Below is my Xenial preseed config (anonymised):
```
#### Contents of the preconfiguration file (for xenial)
### Localization
# Preseeding only locale sets language, country and locale.
d-i debian-installer/locale string en_GB

# Keyboard selection.
# Disable automatic (interactive) keymap detection.
d-i console-setup/ask_detect boolean false
d-i keyboard-configuration/xkb-keymap select gb

### Network configuration
# netcfg will choose an interface that has link if possible. This makes it
# skip displaying a list if there is more than one interface.
d-i netcfg/choose_interface select auto
d-i netcfg/get_hostname string laptop-fresh-install

# If non-free firmware is needed for the network or other hardware, you can 
# configure the installer to always try to load it, without prompting. Or
# change to false to disable asking.
d-i hw-detect/load_firmware boolean true

### Mirror settings
# If you select ftp, the mirror/country string does not need to be set.
d-i mirror/country string manual
d-i mirror/http/hostname string apt.lan.company.com
d-i mirror/http/directory string /ubuntu
d-i mirror/http/proxy string

# Suite to install.
#d-i mirror/suite string xenial
# Suite to use for loading installer components (optional).
#d-i mirror/udeb/suite string xenial
# Components to use for loading installer components (optional).
d-i mirror/udeb/components multiselect main, restricted

### Account setup

d-i passwd/root-login boolean true
d-i passwd/root-password-crypted password crypted-password-string
d-i passwd/make-user boolean false

### Clock and time zone setup
# Controls whether or not the hardware clock is set to UTC.
d-i clock-setup/utc boolean true

# You may set this to any valid setting for $TZ; see the contents of
# /usr/share/zoneinfo/ for valid values.
d-i time/zone string Europe/London

# Controls whether to use NTP to set the clock during the install
d-i clock-setup/ntp boolean true
# NTP server to use. The default is almost always fine here.
d-i clock-setup/ntp-server string ntp.lan.company.com

### Partitioning
#Get around the prompt for UEFI-only
d-i partman-efi/non_efi_system boolean true

#d-i partman-auto/disk string nvme0n1

# In addition, you'll need to specify the method to use.
# The presently available methods are:
# - regular: use the usual partition types for your architecture
# - lvm:     use LVM to partition the disk
# - crypto:  use LVM within an encrypted partition
d-i partman-auto/method string crypto
d-i partman-crypto/passphrase password initial-passphrase
d-i partman-crypto/passphrase-again password initial-passphrase

# If one of the disks that are going to be automatically partitioned
# contains an old LVM configuration, the user will normally receive a
# warning. This can be preseeded away...
d-i partman-lvm/device_remove_lvm boolean true
# The same applies to pre-existing software RAID array:
d-i partman-md/device_remove_md boolean true
# And the same goes for the confirmation to write the lvm partitions.
d-i partman-lvm/confirm boolean true
d-i partman-lvm/confirm_nooverwrite boolean true

# For LVM partitioning, you can select how much of the volume group to use
# for logical volumes.
d-i partman-auto-lvm/guided_size string max

# You can choose one of the three predefined partitioning recipes:
# - atomic: all files in one partition
# - home:   separate /home partition
# - multi:  separate /home, /var, and /tmp partitions
d-i partman-auto/choose_recipe select atomic

# This makes partman automatically partition without confirmation, provided
# that you told it what to do using one of the methods above.
d-i partman-partitioning/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true

### Base system installation
### Apt setup
# You can choose to install restricted and universe software, or to install
# software from the backports repository.
d-i apt-setup/restricted boolean true
d-i apt-setup/universe boolean true
d-i apt-setup/backports boolean true

# Select which update services to use; define the mirrors to be used.
# Values shown below are the normal defaults.
d-i apt-setup/services-select multiselect security
d-i apt-setup/security_host string security.ubuntu.com
d-i apt-setup/security_path string /ubuntu

# Additional repositories, local[0-9] available
d-i apt-setup/local0/repository string deb [arch=amd64] https://download.docker.com/linux/ubuntu xenial stable
d-i apt-setup/local0/comment string Docker
d-i apt-setup/local0/key string http://pxe.lan.company.com/gpg/docker.gpg

d-i apt-setup/local1/repository string deb https://dl.yarnpkg.com/debian/ stable main
d-i apt-setup/local1/comment string Yarn
d-i apt-setup/local1/key string http://pxe.lan.company.com/gpg/yarn.gpg

d-i apt-setup/local2/repository string deb https://deb.nodesource.com/node_6.x xenial main
d-i apt-setup/local2/comment string NodeJS
d-i apt-setup/local2/key string http://pxe.lan.company.com/gpg/nodejs.gpg

d-i apt-setup/local3/repository string deb http://dell.archive.canonical.com/updates/ xenial-dell public
d-i apt-setup/local3/comment string Dell drivers
d-i apt-setup/local3/key string http://pxe.lan.company.com/gpg/dell-ubuntu.gpg

d-i apt-setup/local4/repository string deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main
d-i apt-setup/local4/comment string VS Code
d-i apt-setup/local4/key string http://pxe.lan.company.com/gpg/microsoft.gpg

d-i apt-setup/local5/repository string deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
d-i apt-setup/local5/comment string Google Chrome
d-i apt-setup/local5/key string http://pxe.lan.company.com/gpg/chrome.gpg

d-i apt-setup/local6/repository string deb https://packagecloud.io/slacktechnologies/slack/debian/ jessie main
d-i apt-setup/local6/comment string Slack Desktop app
d-i apt-setup/local6/key string http://pxe.lan.company.com/gpg/slack.gpg

#d-i apt-setup/local2/repository string 
#d-i apt-setup/local2/comment string
#d-i apt-setup/local2/key string

### Package selection
tasksel tasksel/first multiselect ubuntu-desktop

# Whether to upgrade packages after debootstrap.
# Allowed values: none, safe-upgrade, full-upgrade
d-i pkgsel/upgrade select full-upgrade

# Policy for applying updates. May be "none" (no automatic updates),
# "unattended-upgrades" (install security updates automatically), or
# "landscape" (manage system with Landscape).
d-i pkgsel/update-policy select unattended-upgrades

ubiquity ubiquity/success_command string mount -o bind /dev /target/dev; tar xf /cdrom/company/workstation.tbz2 --directory /target/root/; in-target /root/Ubuntu/setup-wrapper.sh; rm /target/root/workstation.tbz2

# Some versions of the installer can report back on what software you have
# installed, and what software you use. The default is not to report back,
# but sending reports helps the project determine what software is most
# popular and include it on CDs.
popularity-contest popularity-contest/participate boolean false

# By default, the system's locate database will be updated after the
# installer has finished installing most packages. This may take a while, so
# if you don't want it, you can set this to "false" to turn it off.
d-i pkgsel/updatedb boolean true

### Boot loader installation
# This is fairly safe to set, it makes grub install automatically to the MBR
# if no other operating system is detected on the machine.
d-i grub-installer/only_debian boolean true

# This one makes grub-installer install to the MBR if it also finds some other
# OS, which is less safe as it might not be able to boot that other OS.
d-i grub-installer/with_other_os boolean true

### Finishing up the installation
# Avoid that last message about the install being complete.
d-i finish-install/reboot_in_progress note
```

Below is the current state of my Bionic preseed (again, anonymised):
```
#### Contents of the preconfiguration file (for xenial)
### Localization
# Preseeding only locale sets language, country and locale.
d-i debian-installer/locale string en_GB

# Keyboard selection.
# Disable automatic (interactive) keymap detection.
d-i console-setup/ask_detect boolean false
d-i keyboard-configuration/xkb-keymap select gb

### Network configuration
# netcfg will choose an interface that has link if possible. This makes it
# skip displaying a list if there is more than one interface.
d-i netcfg/choose_interface select auto
d-i netcfg/get_hostname string laptop-fresh-install

# If non-free firmware is needed for the network or other hardware, you can 
# configure the installer to always try to load it, without prompting. Or
# change to false to disable asking.
d-i hw-detect/load_firmware boolean true

### Mirror settings
# If you select ftp, the mirror/country string does not need to be set.
d-i mirror/country string manual
d-i mirror/http/hostname string apt.lan.company.com
d-i mirror/http/directory string /ubuntu
d-i mirror/http/proxy string

# Suite to install.
#d-i mirror/suite string xenial
# Suite to use for loading installer components (optional).
#d-i mirror/udeb/suite string xenial
# Components to use for loading installer components (optional).
d-i mirror/udeb/components multiselect main, restricted

### Account setup

d-i passwd/root-login boolean true
d-i passwd/root-password-crypted password crypted-password-string
d-i passwd/make-user boolean false

### Clock and time zone setup
# Controls whether or not the hardware clock is set to UTC.
d-i clock-setup/utc boolean true

# You may set this to any valid setting for $TZ; see the contents of
# /usr/share/zoneinfo/ for valid values.
d-i time/zone string Europe/London

# Controls whether to use NTP to set the clock during the install
d-i clock-setup/ntp boolean true
# NTP server to use. The default is almost always fine here.
d-i clock-setup/ntp-server string ntp.lan.company.com

### Partitioning
#Get around the prompt for UEFI-only
d-i partman-efi/non_efi_system boolean true
d-i partman/default_filesystem string ext4
d-i partman-auto/disk string /dev/nvme0n1

# In addition, you'll need to specify the method to use.
# The presently available methods are:
# - regular: use the usual partition types for your architecture
# - lvm:     use LVM to partition the disk
# - crypto:  use LVM within an encrypted partition
d-i partman-auto/method string crypto
d-i partman-crypto/passphrase password initial-passphrase
d-i partman-crypto/passphrase-again password initial-passphrase

# If one of the disks that are going to be automatically partitioned
# contains an old LVM configuration, the user will normally receive a
# warning. This can be preseeded away...
d-i partman-lvm/device_remove_lvm boolean true
# The same applies to pre-existing software RAID array:
d-i partman-md/device_remove_md boolean true
# And the same goes for the confirmation to write the lvm partitions.
d-i partman-lvm/confirm boolean true
d-i partman-lvm/confirm_nooverwrite boolean true

# For LVM partitioning, you can select how much of the volume group to use
# for logical volumes.
d-i partman-auto-lvm/guided_size string max

# You can choose one of the three predefined partitioning recipes:
# - atomic: all files in one partition
# - home:   separate /home partition
# - multi:  separate /home, /var, and /tmp partitions
#d-i partman-auto/choose_recipe select atomic
d-i partman-auto/expert_recipe_file string /cdrom/company/partition-recipe

# This makes partman automatically partition without confirmation, provided
# that you told it what to do using one of the methods above.
d-i partman-partitioning/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true

### Base system installation
### Apt setup
# You can choose to install restricted and universe software, or to install
# software from the backports repository.
d-i apt-setup/restricted boolean true
d-i apt-setup/universe boolean true
d-i apt-setup/backports boolean true

# Select which update services to use; define the mirrors to be used.
# Values shown below are the normal defaults.
d-i apt-setup/services-select multiselect security
d-i apt-setup/security_host string security.ubuntu.com
d-i apt-setup/security_path string /ubuntu

# Additional repositories, local[0-9] available
d-i apt-setup/local0/repository string deb [arch=amd64] https://download.docker.com/linux/ubuntu xenial stable
d-i apt-setup/local0/comment string Docker
d-i apt-setup/local0/key string http://pxe.lan.company.com/gpg/docker.gpg

d-i apt-setup/local1/repository string deb https://dl.yarnpkg.com/debian/ stable main
d-i apt-setup/local1/comment string Yarn
d-i apt-setup/local1/key string http://pxe.lan.company.com/gpg/yarn.gpg

d-i apt-setup/local2/repository string deb https://deb.nodesource.com/node_6.x xenial main
d-i apt-setup/local2/comment string NodeJS
d-i apt-setup/local2/key string http://pxe.lan.company.com/gpg/nodejs.gpg

d-i apt-setup/local3/repository string deb http://dell.archive.canonical.com/updates/ xenial-dell public
d-i apt-setup/local3/comment string Dell drivers
d-i apt-setup/local3/key string http://pxe.lan.company.com/gpg/dell-ubuntu.gpg

d-i apt-setup/local4/repository string deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main
d-i apt-setup/local4/comment string VS Code
d-i apt-setup/local4/key string http://pxe.lan.company.com/gpg/microsoft.gpg

d-i apt-setup/local5/repository string deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
d-i apt-setup/local5/comment string Google Chrome
d-i apt-setup/local5/key string http://pxe.lan.company.com/gpg/chrome.gpg

d-i apt-setup/local6/repository string deb https://packagecloud.io/slacktechnologies/slack/debian/ jessie main
d-i apt-setup/local6/comment string Slack Desktop app
d-i apt-setup/local6/key string http://pxe.lan.company.com/gpg/slack.gpg

#d-i apt-setup/local2/repository string 
#d-i apt-setup/local2/comment string
#d-i apt-setup/local2/key string

### Package selection
tasksel tasksel/first multiselect ubuntu-desktop

# Whether to upgrade packages after debootstrap.
# Allowed values: none, safe-upgrade, full-upgrade
d-i pkgsel/upgrade select full-upgrade

# Policy for applying updates. May be "none" (no automatic updates),
# "unattended-upgrades" (install security updates automatically), or
# "landscape" (manage system with Landscape).
d-i pkgsel/update-policy select unattended-upgrades

ubiquity ubiquity/success_command string mount -o bind /dev /target/dev; tar xf /cdrom/company/workstation.tbz2 --directory /target/root/; in-target /root/Ubuntu/setup-wrapper.sh; rm /target/root/workstation.tbz2

# Some versions of the installer can report back on what software you have
# installed, and what software you use. The default is not to report back,
# but sending reports helps the project determine what software is most
# popular and include it on CDs.
popularity-contest popularity-contest/participate boolean false

# By default, the system's locate database will be updated after the
# installer has finished installing most packages. This may take a while, so
# if you don't want it, you can set this to "false" to turn it off.
d-i pkgsel/updatedb boolean true

### Boot loader installation
# This is fairly safe to set, it makes grub install automatically to the MBR
# if no other operating system is detected on the machine.
d-i grub-installer/only_debian boolean true

# This one makes grub-installer install to the MBR if it also finds some other
# OS, which is less safe as it might not be able to boot that other OS.
d-i grub-installer/with_other_os boolean true

### Finishing up the installation
# Avoid that last message about the install being complete.
d-i finish-install/reboot_in_progress note
```

There are a few differences by now, as a result of my adapting the Bionic config while trying new things. The Xenial config doesn't work with Bionic, and neither does the above - always the same error.

Searching around led me to many configs where the admin had tried to use a disk recipe, so I tried adapting the default Atomic one and adding it to the Bionic config. The recipe I used is:
```
company-partition-recipe ::

1 1 1 free
    $iflabel{ gpt }
    $reusemethod{ }
    method{ biosgrub } .

1024 2048 1536 ext2
    $defaultignore{ }
    $lvmignore{ }
    method{ format }
    format{ }
    use_filesystem{ }
    filesystem{ ext2 }
    mountpoint{ /boot } .

900 10000 -1 $default_filesystem
    $lvmok{ }
    method{ format }
    format{ }
    use_filesystem{ }
    $default_filesystem{ }
    mountpoint{ / } .

100% 512 200% linux-swap
    $defaultignore{ }
    $lvmok{ }
    $reusemethod{ }
    method{ swap }
    format{ } .
```

The PXE rootfs is served via NFS. Unfortunately this means I get very little visibility of what files are being accessed. I think I can change it over to use HTTP so I can consult the access logs to see what files are in use.

A critical problem I keep running into is that there is no way to get any logs out of the OS at this point - with Ubiquity running alone, there is no way to open a graphical terminal, and flipping to a TTY requires a username and password that aren't set. I have a syslog server on my LAN if there's a way to get the installer to dump all messages there.

As a side note, is there any documentation at all on the complete questions Ubiquity supports? I've resorted to reading through the source to little gain; everything is so generic and dynamically assembled that I can't find a concise list of questions.

Many thanks,
Rob

---

### Post by chrysek on 2019-01-18
were you able to figure out the issue with your setup?

---

