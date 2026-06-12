---
title: "Making isolinux boot from existing kernel on hd and launch seed file"
date: 2008-08-01
forum: Installation &amp; Upgrades
---

### Post by tomas_r on 2008-08-01
I'm running Ubuntu 6.06 LTS and have a system installed by a custom made installer. isolinux.cfg appending a preseed/file that launches a bash script after ubuntu is installed.

This works perfectly, but now I'm trying to create an upgrade option in the isolinux.cfg. I just want to insert the dvd, select the upgrade label in isolinux.cfg menu and have it reboot from disk and read an upgrade.seed file which launch an upgrade.sh script by appending a preseed/late_command. I do not want to launch the kernel or installer as I already have a workign os.

More or less I need a bootable cd with a grub-like menu which launches a script at startup. It would be very convenient if I could get the current setup to work by tweaking the isolinux.cfg-file. I have tried the following isolinux.cfg-settings, but when calling localboot, the 'append' part is not launched.

I have this isolinux.cfg:
[FONT="Courier New"]
DEFAULT Upgrade
GFXBOOT bootlogo
APPEND preseed/file=/cdrom/preseed/upgrade.seed initrd=/install/initrd.gz ramdisk_size=16384 root=/dev/ram rw quiet --
LABEL Upgrade1
  menu label ^Upgrade1
  localboot 0x80
  append preseed/file=/cdrom/preseed/upgrade.seed --
LABEL Upgrade2
  menu label ^Upgrade2
  localboot 0x80
  append preseed/file=/cdrom/preseed/upgrade.seed initrd=/install/initrd.gz ramdisk_size=16384 root=/dev/ram rw quiet --
DISPLAY isolinux.txt
TIMEOUT 0
PROMPT 1
F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt
[/FONT]

I have this upgrade.seed:
[FONT="Courier New"]
# Copy the upgrade script
d-i preseed/late_command string /target/cdrom/preseed/late_command_upgrade.sh

# Finish the installation and reboot the system
d-i prebaseconfig/reboot_in_progress note

END
[/FONT]

This is late_command_upgrade.sh:
[FONT="Courier New"]
cp -a /target/cdrom/Upgrade/S99vupgrade /target/etc/rc2.d/
cp -a /target/cdrom/Upgrade/upgrade.sh /target/root/
[/FONT]

S99vupgrade looks like this:
[FONT="Courier New"]
#! /bin/sh
# Remove itself
rm /etc/rc2.d/S99vupgrade
# Start upgrade process
/root/upgrade.sh &
[/FONT]

Some help on how to fix the isolinux.cfg would be greatly appreciated.

---

