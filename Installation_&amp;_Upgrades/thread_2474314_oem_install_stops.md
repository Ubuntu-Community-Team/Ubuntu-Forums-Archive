---
title: "oem install stops"
date: 2022-04-26
forum: Installation &amp; Upgrades
---

### Post by Jaxilian on 2022-04-26
Hi

I used the OEM install on 20.04 LTS and it worked good. Now with 22.04 I tested exacly same seed-file and it stops and waiting for me to choose an option at screen "Updates and other software". I can't find anything about why it stops there. If I choose there and click forward from there, the rest goes automatically like with 20.04.

I know about the new autoinstall, but I am not there yet and this older OEM installation still exist in 22.04 so it should technically work...right?

Anyone know what is wrong?

the file code below

```
# Enable oem install, hide summary screen
d-i oem-config/enable boolean true
d-i ubiquity/summary note

# At the very end of installation:
# - install clamAV
# - finalize OEM install immediately
ubiquity ubiquity/success_command string \
	cp /cdrom/post-install.sh /target/root; \
	chmod 0700 /target/root/post-install.sh; \
	in-target /root/post-install.sh;
	

# Preseeding only locale sets language, country and locale.
# Encoding must be set *somewhere*, such as here, otherwise
# a broken system is produced.
d-i debian-installer/locale string en_US.UTF-8
d-i time/zone string Etc/UTC

# Disable automatic (interactive) keymap detection.
d-i console-setup/ask_detect boolean false
d-i keyboard-configuration/xkb-keymap select us
d-i keyboard-configuration/layoutcode select us

# Silence a bunch of other questions
ubiquity countrychooser/shortlist select US
ubiquity languagechooser/language-name select English
ubiquity localechooser/supported-locales multiselect en_US.UTF-8

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
# https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1329417
# ubiquity ubiquity/poweroff boolean true
```

---

### Post by oasisfai2 on 2022-08-23
I inserted a line in seed-file with down below config, it goes automatically install like with 20.04 . 


ubiquity ubiquity/use_nonfree boolean true

---

