---
title: "Can not boot Mint after unattended install."
date: 2016-07-19
forum: MINT
---

### Post by mint1mint on 2016-07-19
Hi I try to make unattended installation (flash drive with seed file) of Mint 18 and it works on VM but when I launch it on normal desktop it copies files, reboots and shows me only cursor on black screen.
It looks like no boot loader at all. Keeping left Shift key do not show grub menu.
And everything goes fine on VM...
What could it be?

---

### Post by howefield on 2016-07-19
Thread moved to the "*MINT*" sub forum.

---

### Post by mint1mint on 2016-07-20
I've found that GRUB is not installed by ubiquity for some reason.
I use this label in syslinux.cfg:
label install
```
menu label >>> Linux Mint - automatic installation <<<
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/my.seed keyboard-configuration/layoutcode=us boot=casper automatic-ubiquity quiet splash --

```
and this is my.seed
```
#Step 1
d-i debian-installer/locale string ru_RU.UTF-8


#Step 2
d-i time/zone string Europe/Moscow


#Step 3
d-i console-setup/layoutcode string ru
d-i console-setup/toggle select Control+Shift


#Step 4
d-i partman-auto/disk string /dev/sda
d-i partman-auto/method string regular
d-i partman-auto/choose_recipe select atomic
d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true


#Step 5
d-i passwd/user-fullname string myroot
d-i passwd/username string myroot
d-i passwd/user-password Passw0rd Passw0rd
d-i passwd/user-password-again Passw0rd Passw0rd
d-i user-setup/allow-password-weak boolean false
d-i netcfg/get_hostname string mint-fresh
d-i passwd/auto-login boolean false


d-i grub-installer/only_debian boolean true
d-i grub-installer/with_other_os boolean true
ubiquity ubiquity/reboot boolean true
ubiquity ubiquity/poweroff boolean false


#if you want to start commands after the installation
ubiquity ubiquity/success_command string \
cp /cdrom/myscript/ /target/usr/share/ -rf; \
cp /cdrom/myscript/firstrun_launcher /target/etc/init.d/; \
in-target chmod 755 /etc/init.d/firstrun_launcher; \
in-target update-rc.d firstrun_launcher defaults 99; \
df -h >/target/var/log/ubi.log; \
fdisk -l >>/target/var/log/ubi.log; \
mount /dev/sda1 /mnt; \
grub-install --root-directory=/mnt/ /dev/sda
#dd if=/dev/sda bs=512 count=1 2>/dev/null | strings
```

---

### Post by mint1mint on 2016-07-20
Well it seems those strings about installing grub in the end of the script worked and now I have working OS. Thanks to everyone who helped me. Very special thanks to howefield who guided me so nice through difficulties and horrors of Ubuntu.

---

