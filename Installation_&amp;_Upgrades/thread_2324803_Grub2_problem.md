---
title: "Grub2 problem"
date: 2016-05-16
forum: Installation &amp; Upgrades
---

### Post by goblue62 on 2016-05-16
I have successfully installed 16.04 and run update-grub.

The grub configuration file shows 16.04, grub.cfg has three 16.04 entries and I created a copied (from.cfg) grub.d/40_custom entry.

Yet when I restart, the grub menu does not provide Xenial as an option.

Any ideas on the cause and fix of the problem will be appreciated.

---

### Post by yancek on 2016-05-16
You're lacking some information.  Your post would indicate that you just installed Ubuntu 16.04 as the only operating system on the machine.  If that's the case, there would be no reeason to "update-grub" as the installation should create an entries for the Ubuntu install.  There would not be a need for 40_custom entries. What does the grub menuentry show and what else (if anything) is on the computer?

---

### Post by oldfred on 2016-05-16
Standard grub entries just show kernel, not version.
But if you have copied into 40_custom you can edit description at will like these entries.
And you can turn off os-prober, and boot partition entry which is a link to the newest kernel which your own description.

This is just the part of grub with my own entries. I have not turned off os-prober yet, so also have all the standard entries.
```
cat /boot/grub/grub.cfg  | grep menuentry
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
menuentry "Xenial on sdb3" {
menuentry "Wily on sdb9" {
menuentry "trusty 14.04.3 on sdb10" {
menuentry " " {
menuentry 'Live ISOs on SSD' {
menuentry 'Live ISOs on HDD (boot on SSD)' {
menuentry " " {
menuentry "System restart" {
menuentry "System shutdown" {

```

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

---

