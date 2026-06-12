---
title: "Lucid &amp; preseed installation (ubiquity)  question ...."
date: 2010-04-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by uonedang on 2010-04-25
Hi folks

I believe that this is the issue with ubiquity--frontend-gtk ...
I have replaced the use of ubiquity-frontend-gtk  with ubiquity-frontend-kde and it worked fine, 
except the fact that the late-command string does not work ...

I have been searching for solution on the web for the issue with the late_command and tried several
different formats and none of them worked ... 

Please let me know if you got the late_command worked ...

thanks

Dang


--------------------------------------------------------------------------------------------
Hi folks,

I am creating live/installable Lucid ISO image.  I provided the installation with pre-seed file to make automatic installation. 

I see 2 things and the process stops:


1) In the "**Installing System**" pop-up window with "Verifying Installation Configuration" text ...==> the percentage went up to 380% .... 

2) The automatic installation stops at "**Install**" pop-up window.  ... "Ready To Install" ... with "Your new operating system information will now be installed with the following settings" ...  and the information populated properly with information provided in the pre-seed file.

The "**Install**" pop-up window is at  : **Step 1 of 7** and only buttons  "**Quit**" and "**Advanced** ..."  are enabled ....===> can not continue the installation process (even manually ) ...

Is this a ubiquity bug or something wrong with my pre-seed file ?

Any help/suggestion is greatly appreciated ... 

Thanks in advance ...

Dang


++++ Here is the content of my pre-seed file:

[SIZE=1]# Install the SP Linux  - Preseed Information

d-i console-setup/ask_detect boolean false
d-i console-setup/layoutcode string us
d-i debian-installer/locale string en_us
d-i console-keymaps-usb/keymap select mac-usb-us


# Static network configuration.

d-i netcfg/choose_interface select eth0
d-i netcfg/disable_dhcp boolean true
d-i netcfg/get_hostname string my-linux
d-i netcfg/get_nameservers string a.b.c.d
d-i netcfg/get_ipaddress string a.b.c.d
d-i netcfg/get_netmask string 255.255.255.0
d-i netcfg/get_gateway string a.b.c.1
d-i netcfg/confirm_static boolean true

# Clock and time zone 
d-i clock-setup/utc boolean true
d-i time/zone string US/Eastern
d-i clock-setup/ntp boolean false

# Partition 

d-i partman-auto/disk string /dev/sda
d-i partman-auto/method string regular
d-i partman-auto/purge_lvm_from_device boolean true

d-i partman-auto/expert_recipe string boot-root :: 1000 50 1000 ext3 \
    $primary{ } \
    $bootable{ } \
    method{ format } \
    format{ } \
    use_filesystem{ } \
    filesystem{ ext3 } \
    mountpoint{ /boot } \
    . \
    512 512 200% linux-swap \
    method{ swap } \
    format{ } \
    .\
    512 10000 1000000000 ext3 \
    method{ format } \
    format{ } \
    use_filesystem{ } \
    filesystem{ ext3 } \
    mountpoint{ / } \
    .
d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition select Finish partitioning and write changes to disk
d-i partman/confirm boolean true
d-i partman-partitioning/confirm_new_label boolean true

d-i partman/confirm_write_new_label boolean true

# apt-get setup

d-i apt-setup/use_mirror boolean false
d-i apt-setup/local0/repository string  file:///cdrom dists/
d-i apt-setup/local0/comment string This is the mini-repository from the CD iso image

d-i apt-setup/contrib boolean false
d-i apt-setup/use_mirror boolean false

# User Account

d-i passwd/root-login boolean false
d-i passwd/root-password password r00tme
d-i passwd/root-password-again password r00tme

d-i passwd/make-user boolean true
d-i passwd/auto-login string true
d-i passwd/user-fullname string LName FName
d-i passwd/username string myuserId
d-i passwd/user-password password myuserPasswd
d-i passwd/user-password-again password myuserPasswd
d-i passwd/user-uid string 400
d-i passwd/user-default-groups string adm
d-i user-setup/allow-password-weak boolean true

# Installation setup 

d-i grub-installer/only_debian boolean true
d-i finish-install/reboot_in_progress note

# Install additional packages
d-i preseed/late_command string in-target sh /usr/bin/postinstall.sh;


 [/SIZE]

---

