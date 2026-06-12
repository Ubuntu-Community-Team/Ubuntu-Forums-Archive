---
title: "Need help with OEM preseed installations"
date: 2022-03-23
forum: Installation &amp; Upgrades
---

### Post by Jaxilian on 2022-03-23
Hi all

Does anyone have good info on how to automatically install Ubuntu through the OEM and join an Active Directory at the same time in the preseed-file?
I managed to automate it without AD, even with LUKS encryption, but now I need to go in the direction of joining the computer into AD as well.

I have searched so much for info about it but I can't find it.

I hope you can help



edit: Read that debian-installer is deprecated from 20.10.

---

### Post by Jaxilian on 2022-03-24
My ubuntu.seed file for non-encrypted ones. Works great. Just need lines for joining AD now in this code

```
# Enable extras.ubuntu.com.
# d-i	apt-setup/extras	boolean true
# Install the Ubuntu desktop.
# tasksel	tasksel/first	multiselect ubuntu-desktop
# On live DVDs, don't spend huge amounts of time removing substantial
# application packages pulled in by language packs. Given that we clearly
# have the space to include them on the DVD, they're useful and we might as
# well keep them installed.
# ubiquity	ubiquity/keep-installed	string icedtea6-plugin openoffice.org
# d-i  base-installer/kernel/altmeta   string hwe-20.04

# Based on:
# [https://help.ubuntu.com/lts/installation-guide/example-preseed.txt](https://help.ubuntu.com/lts/installation-guide/example-preseed.txt)
# [https://www.chucknemeth.com/debian-9-preseed-uefi-encrypted-lvm/](https://www.chucknemeth.com/debian-9-preseed-uefi-encrypted-lvm/)
# [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/924018/comments/17](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/924018/comments/17)
# [https://github.com/FreeGeekVancouver/preseed-files/blob/master/linux/ubuntu-automatic.cfg](https://github.com/FreeGeekVancouver/preseed-files/blob/master/linux/ubuntu-automatic.cfg)
# and about two dozen other snippets

# There might still be some redundancy in this preseed thanks to Ubiquity
# ignoring some debian-installer questions and expecting answers to its own
# versions of those.

# Enable oem install, hide summary screen
d-i oem-config/enable boolean true
d-i ubiquity/summary note

# At the very end of installation:
# - remove Amazon adware
# - finalize OEM install immediately
ubiquity ubiquity/success_command string \
	cp /cdrom/asset.sh /target/root; \
	cp /cdrom/post-install.sh /target/root; \
	chmod 0700 /target/root/asset.sh; \
	chmod 0700 /target/root/post-install.sh; \
	in-target /root/post-install.sh;
	

# Preseeding only locale sets language, country and locale.
# Encoding must be set *somewhere*, such as here, otherwise
# a broken system is produced.
d-i debian-installer/locale string sv_SE.UTF-8
d-i time/zone string Europe/Stockholm

# language packs
d-i pkgsel/language-packs multiselect se, en

# Disable automatic (interactive) keymap detection.
d-i console-setup/ask_detect boolean false
d-i keyboard-configuration/xkb-keymap select se
d-i keyboard-configuration/layoutcode select se
d-i keyboard-configuration/layout select Swedish
d-i keyboard-configuration/variant select Swedish

# Silence a bunch of other questions
d-i debian-installer/locale string sv_SE.UTF-8
d-i debian-installer/language string sv
d-i debian-installer/country string SE

# netcfg will choose an interface that has link if possible. This makes it
# skip displaying a list if there is more than one interface.
d-i netcfg/choose_interface select auto

# Any hostname and domain names assigned from dhcp take precedence over
# values set here. However, setting the values still prevents the questions
# from being shown, even if values come from dhcp.
# Ultimately none of those even matter in an OEM installation.
d-i netcfg/get_hostname string unassigned-hostname
d-i netcfg/get_domain string unassigned-domain

# If non-free firmware is needed for the network or other hardware, you can
# configure the installer to always try to load it, without prompting. Or
# change to false to disable asking.
d-i hw-detect/load_firmware boolean false

### Mirror settings


# Set password for oem user that will be removed later anyway.
# Without setting the full name, username and password here, the OEM user
# setup dialog is shown during installation.
d-i passwd/user-fullname string OEM
d-i passwd/username string oem
d-i passwd/user-password password oem
d-i passwd/user-password-again password oem
d-i user-setup/allow-password-weak boolean true

################
## DISK SETUP ##
################
d-i partman-auto/init_automatically_partition select Guided - use entire disk
d-i partman-auto/method string regular
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-md/device_remove_md boolean true


# You can choose one of the three predefined partitioning recipes:
# - atomic: all files in one partition
# - home:   separate /home partition
# - multi:  separate /home, /usr, /var, and /tmp partitions
d-i partman-auto/choose_recipe select atomic

d-i partman-partitioning/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true

## END DISK SECTION ##

# The options below come from the regular Ubuntu 18.04 LTS seed

# Enable extras.ubuntu.com.
d-i	apt-setup/extras	boolean true
# Install the Ubuntu desktop.
tasksel	tasksel/first	multiselect ubuntu-desktop
# On live DVDs, don't spend huge amounts of time removing substantial
# application packages pulled in by language packs. Given that we clearly
# have the space to include them on the DVD, they're useful and we might as
# well keep them installed.
ubiquity	ubiquity/keep-installed	string icedtea6-plugin openoffice.org

### Finishing up the installation
# Avoid that last message about the install being complete.
d-i finish-install/reboot_in_progress note
ubiquity ubiquity/reboot boolean true

# Ideally we'd prefer to poweroff, but it doesn't work
# [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1329417](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1329417)
# ubiquity ubiquity/poweroff boolean true
```

---

