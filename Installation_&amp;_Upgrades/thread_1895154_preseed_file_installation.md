---
title: "preseed file installation"
date: 2011-12-14
forum: Installation &amp; Upgrades
---

### Post by kgoedert on 2011-12-14
Hi,

I have a pxe server working with ubuntu orchestra to install my desktop machines (ubuntu-11.10). I imported the alternate iso image to make the installs and its working. I tried then, to customize my preseed/kickstart file as follows: 

```
# Preseeding only locale sets language, country and locale.
d-i debian-installer/locale string en_US
# Enable extras.ubuntu.com.
d-i	apt-setup/extras	boolean true
# Install the Ubuntu desktop.
tasksel	tasksel/first	multiselect ubuntu-desktop
# Keyboard selection.
# Disable automatic (interactive) keymap detection.
d-i console-setup/ask_detect boolean false
d-i keyboard-configuration/layoutcode string br
# Controls whether or not the hardware clock is set to UTC.
d-i clock-setup/utc boolean true
# You may set this to any valid setting for $TZ; see the contents of
# /usr/share/zoneinfo/ for valid values.
d-i time/zone string America/Sao_Paulo
### Account setup
d-i passwd/root-login boolean true
d-i passwd/make-user boolean false
### create a password with `printf "r00tme" | mkpasswd -s -m md5`
d-i passwd/root-password-crypted password $1$ZgNbzcXq$hUR0CnHVtYAvNNNnA2.br1
### Partitioning
d-i partman-auto/disk string /dev/sda
d-i partman-auto/method string regular
d-i partman-auto/purge_lvm_from_device boolean true
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-md/device_remove_md boolean true
d-i partman-lvm/confirm boolean true
d-i partman-auto/choose_recipe select atomic
d-i partman-auto/expert_recipe string                         \
      boot-root ::                                            \
              40 50 100 ext4                                  \
                      $primary{ } $bootable{ }                \
                      method{ format } format{ }              \
                      use_filesystem{ } filesystem{ ext4 }    \
                      mountpoint{ /boot }                     \
              .                                               \
              500 10000 1000000000 ext4                       \
                      method{ format } format{ }              \
                      use_filesystem{ } filesystem{ ext4 }    \
                      mountpoint{ / }                         \
              .                                               \
              64 512 300% linux-swap                          \
                      method{ swap } format{ }                \
              .
# The full recipe format is documented in the file partman-auto-recipe.txt
# included in the 'debian-installer' package or available from D-I source
# repository. This also documents how to specify settings such as file
# system labels, volume group names and which physical devices to include
# in a volume group.
# This makes partman automatically partition without confirmation, provided
# that you told it what to do using one of the methods above.
d-i partman-partitioning/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true
```

The installation goes to the point of the apt packages install and then it hangs. What am I missing on the preseeding file?

Thanks

Kelly

---

