---
title: "autoboot from usb-stick on tablet?"
date: 2015-08-05
forum: Installation &amp; Upgrades
---

### Post by nick208 on 2015-08-05
I run ubuntu desktop from an usb-stick on an acer iconia w700. **Startup Disk Creator** was used to create the install. The tablet has *no way of selecting a boot-option* so I have to plugin an usb-keyboard to boot.
How can I make it boot the first option by default?
Thanks

---

### Post by Bucky Ball on 2015-08-05
Doesn't it boot to the first entry on the grub list if you wait for 10-30 seconds, depending on what you have it set to? When you say you are running Ubuntu from a USB, are you running from a regular live installer USB or you have specifically installed Ubuntu to the USB as a persistence install (which has space to remember settings, tweaks, etc.)?

If you installed to the USB, not just a live installer USB, did you install using EFI mode or legacy?

---

### Post by Bucky Ball on 2015-08-05
Doesn't it boot to the first entry on the grub list if you wait for 10-30 seconds, depending on what you have it set to? When you say you are running Ubuntu from a USB, are you running from a regular live installer USB or you have specifically installed Ubuntu to the USB as a persistence install (which has space to remember settings, tweaks, etc.)?

If you installed to the USB, not just created a live installer USB, did you install using EFI mode or legacy mode set in BIOS?

If the latter, you could try:

```
sudo nano /etc/default/grub
```

... and look for this bit at the top of the file:
```

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
```

Set 'GRUB_TIMEOUT=0' (change last line) and see how you go (make sure to save the changes when you close that file). If it works and you need to get to the grub list at boot again, you will need the keyboard and to hit shift just after the manufacturer splash screen.

---

### Post by sudodus on 2015-08-05
Startup Disk Creator creates a live system that boots via ***syslinux***, not grub. In this case it is a persistent live system. And I don't know how to make such a system autoboot, but I think someone else here at our Ubuntu Forums might know about it.

Let us wait some days for a solution :-)

If no solution is found, I suggest that you backup your casper-rw partition to another drive, and change the system on this pendrive to a ['grub-n-iso'](http://ubuntuforums.org/showthread.php?t=2259682) system, that will boot automatically to the first entry in the grub menu. You may need to edit the grub menu to put the option persistent into the first entry, but that's it.

---

### Post by Bucky Ball on 2015-08-05
> **sudodus said:**
> Startup Disk Creator creates a live system that boots via ***syslinux***, not grub. 

Thanks for that info. :) Been wanting to try Startup Disk Creator ... when I get the time ... :|

---

### Post by nick208 on 2015-08-15
Actually Grub is used (no idea why), it says grub 2 when starting. But when I run ```
sudo update-grub
``` I get ```
/usr/sbin/grub-probe: error: failed to get canonical path of `/cow'.
```

---

### Post by sudodus on 2015-08-17
At the moment I am confused. Please post the output of the following commands in order to make things clear.

```
sudo lsblk -fm
```
and
```
df -h
```

---

### Post by nick208 on 2015-08-19
```
ubuntu@ubuntu:~$ sudo lsblk -fm
NAME   FSTYPE   LABEL    UUID                                 MOUNTPOINT NAME    SIZE OWNER GROUP MODE
sda                                                                      sda    59.6G root  disk  brw-rw----
&#9500;&#9472;sda1 ntfs     Recovery A6FE9AB8FE9A7FEB                                &#9500;&#9472;sda1  400M root  disk  brw-rw----
&#9500;&#9472;sda2 vfat     ESP      F49A-D37B                                       &#9500;&#9472;sda2  100M root  disk  brw-rw----
&#9500;&#9472;sda3                                                                   &#9500;&#9472;sda3  128M root  disk  brw-rw----
&#9500;&#9472;sda4 ntfs     Acer     B8CC9D83CC9D3D16                                &#9500;&#9472;sda4 58.6G root  disk  brw-rw----
&#9492;&#9472;sda5 ntfs              F6B649C3B64984D9                                &#9492;&#9472;sda5  450M root  disk  brw-rw----
sdb                                                                      sdb    14.5G root  disk  brw-rw----
&#9500;&#9472;sdb1 vfat              C72D-FE03                            /cdrom     &#9500;&#9472;sdb1  4.9G root  disk  brw-rw----
&#9492;&#9472;sdb2 ext4     casper-rw
                         16d08e72-9e7f-4717-a9b2-c2781693eef7 /media/ubu &#9492;&#9472;sdb2  9.6G root  disk  brw-rw----
loop0  squashfs                                               /rofs      loop0     1G root  disk  brw-rw----

```
```

ubuntu@ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G     0  1.9G   0% /dev
tmpfs           377M  5.9M  371M   2% /run
/dev/sdb1       4.9G  1.1G  3.9G  23% /cdrom
/dev/loop0      1.1G  1.1G     0 100% /rofs
/cow            9.4G  4.1G  4.8G  47% /
tmpfs           1.9G  328K  1.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
tmpfs           1.9G  4.0K  1.9G   1% /tmp
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           377M   36K  377M   1% /run/user/999
/dev/sdb2       9.4G  4.1G  4.8G  47% /media/ubuntu/casper-rw

```

I may have done something unorthodox trying to fix the problem with grub and autostart. Maybe just aswell restart?

---

### Post by sudodus on 2015-08-20
I think I understand the situation now: You are booting the live drive in UEFI mode.

A live drive created with the Startup Disk Creator boots via syslinux in BIOS mode and via grub 2 in UEFI mode.

I don't think you can modify grub via /etc/default/grub. That method works only in regular installed systems. But often grub 2 will use a simple grub.cfg file, where you can add or modify a couple of lines directly:

```
set timeout=10
set default=0
```

The 'timeout' variable decides how long the grub menu will be shown before auto-starting the default application.

The 'default' variable decides which of the alternatives (lines in the grub menu) that will be auto-started. 0 means the first line, 1 means the second line etc.

This works for me in the system that I have made for the [bleeding edge version of mkusb](https://help.ubuntu.com/community/mkusb#mkusb_version_10).

---

### Post by sudodus on 2015-08-20
I used the **Startup Disk Creator** and created a USB pendrive with **ubuntu-14.04.2-desktop-amd64.iso**.

Then I edited the file /cdrom/boot/grub/grub.cfg to be the following (added the [COLOR="#008000"]**green lines**[/COLOR]). It works for me in UEFI mode :-)

```
[COLOR="#008000"][B]set timeout=10
set default=0[/B][/COLOR]

if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

[COLOR="#008000"][B]menuentry "Run Ubuntu persistent live" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash persistent --
	initrd	/casper/initrd.lz
}
[/B][/COLOR]menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}
```

***Edit:*** But I think it is easier to use [mkusb version 10](https://help.ubuntu.com/community/mkusb#mkusb_version_10) ;-)

---

