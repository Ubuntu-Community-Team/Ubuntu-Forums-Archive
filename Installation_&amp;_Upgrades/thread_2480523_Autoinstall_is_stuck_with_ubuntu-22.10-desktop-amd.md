---
title: "Autoinstall is stuck with ubuntu-22.10-desktop-amd64.iso"
date: 2022-11-01
forum: Installation &amp; Upgrades
---

### Post by rain4 on 2022-11-01
Problem:
Autoinstall stop on the phase "Updates and other software" as attached screenshot shows with ubuntu-22.10-desktop-amd64.iso.
After click "Continue" button, the autoinstall will go on and finish the unattended installtion
 Details:
I modify the files /preseed/ubuntu.seed and /boot/grub/grub.cfg inside ubuntu-22.10-desktop-amd64.iso for the unattended install.
 With the modified ISO, the autoinstall begins but stop on the phase "Updates and other software" as attached screenshot shows.
After click "Continue" button, the autoinstall can go on and finish the unattended installation.
 Content of /preseed/ubuntu.seed:
### step 1 : Localization
d-i debian-installer/locale string en_US
ubiquity languagechooser/language-name select English (US)
ubiquity countrychooser/shortlist select US
ubiquity localechooser/supported-locales multiselect en_US.UTF8
 # Step 2 keyboard
ubiquity keyboard-configuration/layoutcode select us
d-i console-setup/ask_detect boolean false
d-i keyboard-configuration/xkb-keymap select us
 # Step 3 install Mode
ubiquity ubiquity/minimal_install boolean true
ubiquity ubiquity/download_updates boolean false
ubiquity/use_nonfree boolean false
 #step 4 disk
ubiquity partman-auto/disk string /dev/sda
ubiquity partman-auto/method string regular
ubiquity partman-lvm/device_remove_lvm boolean true
ubiquity partman-md/device_remove_md boolean true
ubiquity partman-auto/choose_recipe select atomic
 # This makes partman automatically partition without confirmation
d-i partman-partitioning/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true
 #step 5 : time/zone
d-i time/zone string Asia/Shanghai
d-i clock-setup/utc-auto boolean true
d-i clock-setup/utc boolean true
d-i clock-setup/ntp boolean true
d-i clock-setup/ntp-server ntp.vmware.com
 ### step 6 Account setup
.....
.....
.....
 Note:
with the same file /preseed/ubuntu.seed, autoinstall can works well with ubuntu-18.04-desktop-amd64.iso.
But it stop on "Step 3" with ubuntu-22.10-desktop-amd64.iso/ubuntu-20.04.5-desktop-amd64.iso
 Not sure it's the issue about /preseed/ubuntu.seed or ubiquity installer.
Would someone help me with it ?  Thanks

---

