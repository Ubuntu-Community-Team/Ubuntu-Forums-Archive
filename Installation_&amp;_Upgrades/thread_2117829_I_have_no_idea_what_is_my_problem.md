---
title: "I have no idea what is my problem"
date: 2013-02-19
forum: Installation &amp; Upgrades
---

### Post by miralaba on 2013-02-19
So... how you can see with this title, I am a very new user of linux! let me explain what happens:

my notebook have had the hd broken and I am trying to use an external hd. When I boot I have an error message:


"Gave up waiting for root device. common problems:
 - boot args (cat /proc/cmdline)
      -check rootdelay= (did the system wait long enough?)
      -check root= (did the system wait for right devices?)
 - missing modules (cat /proc/modules; ls /dev)

ALERT! /dev/disk/by-uuid/b9c91e7c-5ed4-40ad-aecf-7894d246182c does not exist.

BusyBox v1.19.3 (Ubuntu1: 1.19.3 - 7Ubuntu1) built-in shel (ash)
enter 'help' for a list of built-in commands

(initramfs) ATA_ID[236]: HDIO_GET_IDENTITY failed for '/dev/sda': invalid argument"


for now, I am using a USB linux
and I hope someone could help me
thanks a lot

---

### Post by dino99 on 2013-02-19
well, as the internal drive is broken, and i suppose having ubuntu installed on it with the grub bootloader, now it fail of course. You need to do an install on the external drive:

an example:
[http://ubuntuforums.org/showpost.php?p=11729309&postcount=6](http://ubuntuforums.org/showpost.php?p=11729309&postcount=6)

my way for installation:
[http://ubuntuforums.org/showpost.php?p=12495221&postcount=2](http://ubuntuforums.org/showpost.php?p=12495221&postcount=2)

[http://askubuntu.com/questions/239871/how-to-make-an-ubuntu-installation-on-external-hdd-boot-on-any-system](http://askubuntu.com/questions/239871/how-to-make-an-ubuntu-installation-on-external-hdd-boot-on-any-system)

\\:D/

---

### Post by miralaba on 2013-02-19
Actually, I have installed the Ubuntu after the internal hd broken. And I have done from this USB linux, so this processes was automatic and the grub bootloader are in the external hd.

I think the problem is with the grub files... I have done some researches before to ask help and I suppose the trouble is with something like 'ismode part_msdos1', 'ismod ext2' [but I configure the hd to ext4] and  'set root=hd1,msdos1' in the grub.cfg.....

---

### Post by darkod on 2013-02-19
First, the grub2 bootloader can still end up on /dev/sda, the internal disk, because it detects it as first disk.

Second, sometimes the computer doesn't detect usb hdds fast enough to boot from them. This could be your issue.

Try booting and entring into bios. You don't need to change anything in bios (except set usb hdd as first boot option unless you already did that). Let it stay 15-20sec on the bios page so that the usb hdd gets power. Then go out of the bios and see if it boots.

Also, from live mode in terminal run:
sudo blkid

and compare that UUID in the error message with your partitions. Is it looking for some partition on the internal or ext hdd?

---

