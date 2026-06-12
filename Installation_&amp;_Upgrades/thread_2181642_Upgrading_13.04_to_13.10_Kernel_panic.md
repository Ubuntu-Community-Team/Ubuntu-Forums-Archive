---
title: "Upgrading 13.04 to 13.10 Kernel panic"
date: 2013-10-18
forum: Installation &amp; Upgrades
---

### Post by Pawello on 2013-10-18
During an upgrade from 13.04 to 13.10 I got: Kernel panic-not syncing: VFS: unable to mount root fs on unknown block(0,0). I manually switched off the power of my laptop. Since then I'm not able to boot Ubuntu - this error appears every time I boot.

I've been using e4rat instead of ureadahead before upgrading.

---

### Post by Pawello on 2013-10-18
[SIZE=2][FONT=arial]All right, I've managed to solve my problem with a great help from rafalcieslak.

The situation: Kernel panic during upgrade from Ubuntu 13.04 to 13.10 (described above).

What to do:
At first to boot to system I needed to follow [http://askubuntu.com/questions/41930/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block0-0](http://askubuntu.com/questions/41930/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block0-0)
> Start with a livecd, open a a terminal[/FONT][/SIZE]> [SIZE=2][FONT=arial]sudo fdisk -l
sudo mount /dev/sdax /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt 
[/FONT][/SIZE][COLOR=#333333][FONT=UbuntuRegular][SIZE=2][FONT=arial]and now you can make update-initramfs and update-grub without errors[/FONT][/SIZE][/FONT][/COLOR]
[SIZE=2][FONT=arial]update-initramfs -u -k 2.6.38-8-generic (or your version)
update-grub2
[/FONT][/SIZE][FONT=UbuntuRegular][FONT=arial][COLOR=#333333]And reboot your system[/COLOR][/FONT][/FONT][FONT=UbuntuRegular][FONT=arial]
[COLOR=#333333]This allowed me to boot Ubuntu.[/COLOR]

[COLOR=#333333]Then I happened to have a problem with sudo apt-get something. I was shown a message:[/COLOR][SIZE=2][COLOR=#333333] "E: dpkg was interrupted, **you must manually run 'dpkg --configure -a' to correct the problem."**[/COLOR][/SIZE][COLOR=#333333]I run suggested command and got kernel panic as before.[/COLOR]
[COLOR=#333333]I booted Ubuntu with "--no-log" parameter in GRUB's entry (because [/COLOR][/FONT][/FONT][https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1120660](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1120660))[FONT=UbuntuRegular][FONT=arial][COLOR=#333333]. This let me reconfigure dpkg with proposed command: "[/COLOR][COLOR=#333333]dpkg --configure -a" without kernel panic, finally.


[/COLOR][COLOR=#262626]The last thing to do was:
[/COLOR][/FONT][/FONT]
[COLOR=#262626][FONT=arial]sudo apt-get update
[/FONT][/COLOR]
[COLOR=#262626][FONT=arial]sudo apt-get dist-upgrade

That's it.
[/FONT][/COLOR]

---

