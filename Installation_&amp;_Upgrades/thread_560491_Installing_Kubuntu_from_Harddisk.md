---
title: "Installing Kubuntu from Harddisk"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by hammadmirza on 2007-09-26
Hello,
i am new to Linux...but used Mac & windows....
in my laptop i want to installl Kubuntu....my laptop dvdrom is in bad condition and doesnt boots from cd...so tell me how can i install kubuntu by copying cd contents to laptop harddisk and installing it....

Remember: my laptop has no OS installed yet....blank HDD

[I]I have tried this but doesnt works:
copied ntldr and other things required to boot of Windows XP
and in boot.ini i have and entry to load GRUB FOR DOS, and in menu.lst of GRUB i have such 2 entries:
**title Install Linux**
kernel (hd0,0)/boot/vmlinuz
initrd (hd0,0)/boot/initrd.gz
**Not works**

**title Install Linux2**
    DEFAULT /casper/vmlinuz
GFXBOOT bootlogo
APPEND  preseed/file=/cdrom/preseed/kubuntu.seed boot=casper initrd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL live
  menu label ^Start or install Kubuntu
  kernel /casper/vmlinuz
  append  preseed/file=/cdrom/preseed/kubuntu.seed boot=casper initrd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL xforcevesa
  menu label Start Kubuntu in safe ^graphics mode
  kernel /casper/vmlinuz
  append  preseed/file=/cdrom/preseed/kubuntu.seed boot=casper xforcevesa initrd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL check
  menu label ^Check CD for defects
  kernel /casper/vmlinuz
  append  boot=casper integrity-check initrd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL memtest
  menu label ^Memory test
  kernel /install/mt86plus
  append -
LABEL hd
  menu label ^Boot from first hard disk
  localboot 0x80
  append -
DISPLAY isolinux.txt
TIMEOUT 300
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

** error:  kernel panic - no syncing: VFS: Unable to mount root fs on unknown-block (8, 3) **


[/I]

---

### Post by kellemes on 2007-09-26
You have a couple of options, [see here]("https://help.ubuntu.com/community/Installation#head-ca8e337bdfab6bfa1d064371898775fe1e9e22fd").

---

