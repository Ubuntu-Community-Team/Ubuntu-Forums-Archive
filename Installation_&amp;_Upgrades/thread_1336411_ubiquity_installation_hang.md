---
title: "ubiquity installation hang"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by uonedang on 2009-11-24
Hi all,

I am having  an issue with automatic installation of the customised ubuntu (9.10) 
with preseed information.  If I install this iso manually .... everything went OK ... 

My preseed file content is as following: [ I ran this using kmv/qemu]
 
====================================================[INDENT][SIZE=1]# Installation Pre-seed Information

d-i debian-installer/locale string en_US

d-i console-setup/ask_detect boolean false
d-i console-setup/layoutcode string us


# Static network configuration.
d-i netcfg/get_hostname string myserver
d-i netcfg/get_nameservers string myserver
d-i netcfg/get_ipaddress string 192.0.2.15
d-i netcfg/get_netmask string 255.255.255.0
d-i netcfg/get_gateway string 192.0.2.1
d-i netcfg/confirm_static boolean true

# Clock and time zone 
d-i clock-setup/utc boolean false
d-i time/zone string US/Eastern
d-i clock-setup/ntp boolean false

# Partition 

d-i partman-auto/disk string /dev/sda
d-i partman-auto/method string  regular

d-i partman-auto/choose_recipe select atomic

d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true

# User Account

d-i passwd/root-login boolean false
d-i passwd/root-password password r00tme
d-i passwd/root-password-again password r00tme

d-i passwd/make-user boolean true
d-i passwd/user-fullname string MY NAME
d-i passwd/username string myname
d-i passwd/user-password password myname123
d-i passwd/user-password-again password myname123
d-i passwd/user-uid string 400
d-i passwd/auto-login string true
d-i passwd/user-default-groups string adm
d-i user-setup/allow-password-weak boolean true

d-i finish-install/reboot_in_progress note
[/SIZE][/INDENT]=======================================

It hangs in the window: "Checking the Installation"   (detecting the file systems) which is 100% complete ...

I modified: /lib/partman/recipes/30atomic to replace exrt2 with ext3 ... 

Any suggestion ? ... Anything wrong in the preseed file ?

Thanks in advance ..

Dang

---

### Post by uonedang on 2009-11-25
Hi,

I have modified the preseed file:
=====================================================[INDENT][SIZE=1]# Install the SP Linux  - Preseed Information[/SIZE]

[SIZE=1]d-i debian-installer/locale string en_US[/SIZE]

[SIZE=1]d-i console-setup/ask_detect boolean false[/SIZE]
[SIZE=1]d-i console-setup/layoutcode string us[/SIZE]


[SIZE=1]# Static network configuration.[/SIZE]
[SIZE=1]d-i netcfg/get_hostname string myserver[/SIZE]
[SIZE=1]d-i netcfg/get_nameservers string myserver[/SIZE]
[SIZE=1]d-i netcfg/get_ipaddress string 192.0.2.15[/SIZE]
[SIZE=1]d-i netcfg/get_netmask string 255.255.255.0[/SIZE]
[SIZE=1]d-i netcfg/get_gateway string 192.0.2.2[/SIZE]
[SIZE=1]d-i netcfg/confirm_static boolean true[/SIZE]

[SIZE=1]# Clock and time zone [/SIZE]
[SIZE=1]d-i clock-setup/utc boolean false[/SIZE]
[SIZE=1]d-i time/zone string US/Eastern[/SIZE]
[SIZE=1]d-i clock-setup/ntp boolean false[/SIZE]

[SIZE=1]# Partition [/SIZE]

[SIZE=1]d-i partman-auto/init_automatically_partition[/SIZE]
[SIZE=1]d-i partman-auto/disk string /dev/sda[/SIZE]
[SIZE=1]d-i partman-auto/method string regular[/SIZE]

[SIZE=1]d-i partman-auto/expert_recipe string boot-root :: 1000 50 1000 ext3 \[/SIZE]
[SIZE=1]    $primary{ } \[/SIZE]
[SIZE=1]    $bootable{ } \[/SIZE]
[SIZE=1]    method{ format } \[/SIZE]
[SIZE=1]    format{ } \[/SIZE]
[SIZE=1]    use_filesystem{ } \[/SIZE]
[SIZE=1]    filesystem{ ext3 } \[/SIZE]
[SIZE=1]    mountpoint{ /boot } \[/SIZE]
[SIZE=1]    . \[/SIZE]
[SIZE=1]    512 512 200% linux-swap \[/SIZE]
[SIZE=1]    method{ swap } \[/SIZE]
[SIZE=1]    format{ } \[/SIZE]
[SIZE=1]    . \[/SIZE]
[SIZE=1]    512 10000 5000 ext3 \[/SIZE]
[SIZE=1]    method{ format } \[/SIZE]
[SIZE=1]    format{ } \[/SIZE]
[SIZE=1]    use_filesystem{ } \[/SIZE]
[SIZE=1]    filesystem{ ext3 } \[/SIZE]
[SIZE=1]    mountpoint{ / } \[/SIZE]
[SIZE=1]    . [/SIZE]

[SIZE=1]d-i partman/confirm_write_new_label boolean true[/SIZE]
[SIZE=1]d-i partman/choose_partition select Finish partitioning and write changes to disk[/SIZE]
[SIZE=1]d-i partman/confirm boolean true[/SIZE]

[SIZE=1]# Installation setup [/SIZE]

[SIZE=1]popularity-contest popularity-contest/participate boolean false[/SIZE]
[SIZE=1]d-i grub-installer/only_debian boolean true[/SIZE]

[SIZE=1]# User Account[/SIZE]

[SIZE=1]d-i passwd/root-login boolean false[/SIZE]
[SIZE=1]d-i passwd/root-password password r00tme[/SIZE]
[SIZE=1]d-i passwd/root-password-again password r00tme[/SIZE]

[SIZE=1]d-i passwd/make-user boolean true[/SIZE]
[SIZE=1]d-i passwd/user-fullname string My Linux[/SIZE]
[SIZE=1]d-i passwd/username string mylinux[/SIZE]
[SIZE=1]d-i passwd/user-password password mylinux123[/SIZE]
[SIZE=1]d-i passwd/user-password-again password mylinux123[/SIZE]
[SIZE=1]d-i passwd/user-uid string 400[/SIZE]
[SIZE=1]d-i passwd/auto-login string true[/SIZE]
[SIZE=1]d-i passwd/user-default-groups string adm[/SIZE]
[SIZE=1]d-i user-setup/allow-password-weak boolean true[/SIZE]

[SIZE=1]d-i finish-install/reboot_in_progress note[/SIZE]
[/INDENT]======================================================

The installation ran ... and it stopped at "Ready To Install" window ... the window presented the configuration as specified in the preseed file ... everything looked OK ... 

But the "Back" and "Install" buttons were disabled .. only "Quit" and "Advance" button were enabled ...  At the bottom right of the window, it says "***Step 1 of 6***" ..... which is not the right step number ...

I can not proceed with the installation ... since the Install button is disabled ... Is there something missing or incorrect from the preseed file ? Is there anyway that I can by pass this window and complete the installation without user input?

Thanks,

Dang

---

### Post by uonedang on 2009-11-30
Hi folks,

If I run the installation with  option "noninteractive" ... everything is installed properly with the pre-seeded  information to the end and the box is rebooted ..... but it has a blank screen during the installation process. ... I really want to see the working progress of the installation process ... I have been looking at the */frontend/*.py files, especially the gtk_ui.py  ... but not sure where to modify for testing purpose ... 

Any suggestion?

Thanks

Dang

---

