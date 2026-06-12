---
title: "Ubuntu Desktop Preseed Answers for semi automated install"
date: 2017-03-30
forum: Installation &amp; Upgrades
---

### Post by shawn.c on 2017-03-30
Hey guys, 

I am trying to do a semi automated install of Ubuntu 16.04 Desktop iso image.
What I was trying to achieve was to preseed answers to all the question asked during installation and users only have to click continue to proceed with the installation.

The file I have edited are 
```
isofile/boot/grub/grub.cfg
```
since I am using efi boot. 
```
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/ks.preseed debian-installer/locale?=en_SG keyboard-configuration/layoutcode?=us ubiquity/reboot=true languagechooser/language-name=English countrychooser/shortlist=SG localechooser/supported-locales?=en_SG.UTF-8 boot=casper automatic-ubiquity initrd=/casper/initrd.lz quiet splash ---
    initrd    /casper/initrd.lz
}
```
and my ks.preseed file
```
# Locale
d-i debian-installer/locale string en_SG
d-i debian-installer/locale seen false
d-i console-setup/ask_detect boolean false
d-i console-setup/layoutcode string us
d-i console-setup/layoutcode seen false
# Network
d-i netcfg/get_hostname string ComputerName
#d-i netcfg/get_domain string 
d-i netcfg/choose_interface select auto
# Clock
d-i clock-setup/utc-auto boolean true
d-i clock-setup/utc boolean true
d-i time/zone string Singapore
d-i time/zone seen false
d-i clock-setup/ntp boolean true
# Users
d-i passwd/user-fullname string Name
d-i passwd/user-fullname seen false
d-i passwd/username string User123
d-i passwd/username seen false
d-i passwd/user-password-crypted password <Used mkpasswd for a crypt 3 password>
d-i passwd/user-password crypted seen false
d-i passwd/user-default-groups string adm audio cdrom dip lpadmin sudo plugdev sambashare video
d-i passwd/root-login boolean false
#d-i passwd/root-password-crypted password rootEncryptedPasswd
#d-i user-setup/allow-password-weak boolean true

```
I was able to set default answer for Language/TimeZone/Keyboard. 
However when it comes to the create user page. It seems that only the full name row is filled correctly where the Computer Name / Username is filled in incorrectly and the password options being blank(unfilled). 
Is there something missing to my file?

---

### Post by aave on 2017-07-07
Hey, have you found out a solution for your problem? I am having similar problems than you and my system boots for 2 times when i am using my automated installer from USB stick (first time it creates user from presseed file and second time it asks the user settings). Did you shawn have any problems of this type?

---

