---
title: "Odd use of livecd yields odd results - oddly enough."
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by kaffemonster on 2010-03-17
Sorry about the oddities...


I have installed Grub on a bootable USB stick to have it boot several different ISO's - Ubuntu, UBCD, Hirens etc. Hirens, UBCD and Win7 isos just work but when I select Ubuntu, I get the menu and all, but when I select "Try without any..." or "Install Ubuntu", the screen just goes black after a few seconds with the ubuntu logo centered on screen.

The "Test CD for defects" option does the same :(

Menu.lst on the usb key looks like this:
```
color light-gray/blue black/light-gray
timeout 30
default /default

title UBCD 4.11
fallback 1
find --set-root /boot_isos/ubcd411.iso
map /boot_isos/ubcd411.iso (0xff) || map --mem /boot_isos/ubcd411.iso (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title Hirens Boot CD 10.2
fallback 2
find --set-root /boot_isos/hirens.iso
map /boot_isos/hirens.iso (0xff) || map --mem /boot_isos/hirens.iso (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title Ubuntu 9.10 32 Bit
fallback 3
find --set-root /boot_isos/ubuntu-9.10-desktop-i386.iso
map /boot_isos/ubuntu-9.10-desktop-i386.iso (0xff) || map --mem /boot_isos/ubuntu-9.10-desktop-i386.iso (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title Ubuntu 9.10 64 Bit
fallback 4
find --set-root /boot_isos/ubuntu-9.10-desktop-amd64.iso
map /boot_isos/ubuntu-9.10-desktop-amd64.iso (0xff) || map --mem /boot_isos/ubuntu-9.10-desktop-amd64.iso (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title Windows 7 32 Bit
fallback 5
find --set-root /boot_isos/win7_32.iso
map /boot_isos/win7_32.iso (0xff) || map --mem /boot_isos/win7_32.iso (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title Windows 7 64 Bit
fallback 6
find --set-root /boot_isos/win7_64.iso
map /boot_isos/win7_64.iso (0xff) || map --mem /boot_isos/win7_64.iso (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title commandline
commandline

title reboot
reboot
```

---

### Post by kaffemonster on 2010-03-17
Just tried changing the file name from ubuntu-9.10-desktop-i386.iso to ubu910_32.iso and now I get an error message in stead of the black screen:

```
(initramfs) Unable to find a medium containing a live file system
```

---

