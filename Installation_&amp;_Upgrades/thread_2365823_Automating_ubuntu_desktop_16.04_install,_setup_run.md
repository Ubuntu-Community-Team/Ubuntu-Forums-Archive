---
title: "Automating ubuntu desktop 16.04 install, setup running two times"
date: 2017-07-11
forum: Installation &amp; Upgrades
---

### Post by aave on 2017-07-11
[COLOR=#111111][FONT=Ubuntu]Pretty new to the ubuntu scene and i'm trying to automate the install of a ubuntu 16.04 desktop. I have managed to get my install process to the point that it uses preseed values to answer all of the questions during the install process. Then the system restarts but then my problem emerges: it asks the user configuration questions again. So it first runs a window with a title "install (as superuser)" and the second window is called "system configuration". After I have answered the questions again and the system reboots i have two users in the login screen, the preseeded one and the one i manually had to do. Anyone has any insight to my problem?

Grub.cfg (Booting efi USB):

[/FONT][/COLOR]```
[COLOR=#111111][FONT=Ubuntu]if loadfont /boot/grub/font.pf2 ; then [/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]set gfxmode=auto 
insmod efi_gop 
insmod efi_uga 
insmod gfxterm 
terminal_output gfxterm 
fi 
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]set menu_color_normal=white/black 
set menu_color_highlight=black/light-gray[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]set timeout=0 set default="0"[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]menuentry "Start " { set gfxpayload=keep linux /casper/vmlinuz boot=casper file=/cdrom/install/preseed.cfg automatic-ubiquity quiet noprompt auto=ture priority=critical ubiquity/reboot=true noshell splash languagechooser/language-name=English -- 
initrd /casper/initrd.lz[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]}[/FONT][/COLOR]
```

preseed.cfg
[COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR]```

[COLOR=#111111][FONT=Ubuntu]Networking
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]d-i netcfg/choose_interface select auto 
d-i netcfg/disable_dhcp boolean false 
d-i netcfg/wireless_wep string 
d-i netcfg/dhcp_options select 
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Do not configure the network at this time
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]d-i netcfg/dhcp_failed note 
d-i netcfg/dhcp_timeout string 3 
d-i netcfg/get_hostname string ubuntu 
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Do not filter out disks with mounted partitions.
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]d-i partman/filter_mounted boolean false 
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Remove existing software RAID partitions if they exist.
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]d-i partman-md/device_remove_md boolean true 
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Do not encrypt user's home directory.
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]d-i user-setup/encrypt-home boolean false 
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Do not require mount points for partitions with filesystems.
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]d-i partman-basicfilesystems/no_mount_point boolean false 
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]non-efi system
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]d-i partman-efi/non_efi_system boolean true 
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]select built-in emmc device[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]d-i partman-auto/disk string /dev/mmcblk0 
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]use the usual partition types for your architecture
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]d-i partman-auto/method string regular[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]no swap partition
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]d-i partman-basicfilesystems/no_swap boolean false[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]use full emmc and only have one partition
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]d-i partman-auto/expert_recipe string \ 
efi-root :: \ 
256 300 512 free \ 
$iflabel{ gpt } \ 
method{ efi } format{ } \ 
. \ 
4000 10000 -1 ext4 \ 
$primary{ } \ 
method{ format } format{ } \ 
use_filesystem{ } filesystem{ ext4 } \ 
mountpoint{ / } \ 
. 
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]select disk recipe listed above
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]d-i partman-auto/choose_recipe select efi-root 
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Partition without confirmation
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]d-i partman/confirm_write_new_label boolean true 
d-i partman/choose_partition select 
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Finish partitioning and write changes to disk
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]d-i partman/confirm_nooverwrite boolean true 
d-i partman/confirm boolean true 
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Boot loader This one makes grub-installer install to the MBR even if it finds some other OS
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]d-i grub-installer/with_other_os boolean true 
d-igrub-installer/only_debian boolean false 
d-i grub-installer/bootdev string /dev/mmcblk0 
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Keyboard selection
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]d-i keyboard-configuration/layoutcode string us 
d-i keyboard-configuration/variantcode string 
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Local
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]d-i debian-installer/locale string en_US.UTF-8 
d-i debian-installer/locale seen true 
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Timezone
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]d-i clock-setup/utc-auto boolean true 
d-i clock-setup/utc boolean true 
d-i time/zone string US/Pacific 
d-i clock-setup/ntp boolean true 
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]disable automatic keymap detection
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]d-i console-setup/ask_detect boolean false 
d-i console-setup/layoutcode string us 
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]User Creation
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]d-i passwd/root-login boolean false 
d-i passwd/user-fullname string fullname 
d-i passwd/user-fullname seen true 
d-i passwd/username string user 
d-i passwd/username seen true 
d-i passwd/user-password password 1234 
d-i passwd/user-password-again password 1234 
d-i passwd/user-password seen true 
d-i passwd/auto-login boolean true [/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]d-i user-setup/allow-password-weak boolean true
 [/FONT][/COLOR]
```[COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]

[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]Could the issue be related to the command generating the .iso file with the command 
```
mkisofs -U -A "Desktop" -V "Desktop" -volset "Desktop" -J -joliet-long -r -v -T -o /opt/Desktop.iso -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -eltorito-alt-boot -e boot/grub/efi.img -no-emul-boot /opt/desktop.
```[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu] This makes iso file to to boot from first from efi device(usb stick) and then mbr? Could it tbe that the mbr doesn't hold the preseed values?

Thanks for the answers in advance :)[/FONT][/COLOR]

---

