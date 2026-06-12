---
title: "Grub 2 - strange behaviour on boot"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by Richard1979 on 2010-02-09
This is a bit of a strange one.
When I start up and it gets to "Grub loading..." I have a lot of hard disk activity but I can tell it's not normal because it has short pulses as if it's in an infinite loop.
My system does boot eventually but it pauses on this bit for a good 4-5 seconds and it never did this on my last install.

Any ides what it could be? 
Maybe it's the /home decrypting but I don't think I set it to be encrypted when I installed.
I'm running kernel 2.6.31-19.

---

### Post by BigSteve_G on 2010-02-09
Is ubuntu (well the /boot directory) on the first drive you are booting from?

I've had this problem myself with Ubuntu (& the /boot) installed on a different drive then the 1 I was booting from but when installed on the same drive no problem.

From what I've read on a search around google its something to do with grub having problems with going looking on other drives (30 sec wait in most cases)

-My advice Linux Mint 7 - works a treat & looks good

---

### Post by Richard1979 on 2010-02-09
I think that's my problem:
```

root@lara:/home/richard# fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xad6496c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121601   976760001   83  Linux

Disk /dev/sdb: 74.4 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x50505050

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        8511    68364576   83  Linux
/dev/sdb2            8512        9039     4241160    5  Extended
/dev/sdb5            8512        9039     4241128+  82  Linux swap / Solaris

(some of /etc/fstab)

# / was on /dev/sdb1 during installation
UUID=ea5e4be9-fc0d-4732-af0a-37c5fc492c74 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda1 during installation
/dev/sda1     /home           ext3    defaults        0       0




```Damn, looks like I'll have to reinstall Grub into sdb1 because that one is my / where sda1 is my /home

---

### Post by jenaniston on 2010-02-09
The grub installed to my Ubuntu 9.10 x86_64 USB drive /dev/sdb is called "GNU grub version 1.97~_beta4_"

Unless you go into Advanced Options at last step of install from the live CD iso .  . .
it will* default* grub install to a different drive - like /dev/hd**a** by default.

I know that the grub version with U9.04 Live "installer to hard disk"  did*** not*** virtually hide this default - 
it clearly upfront showed where it defaulted the grub bootloader install location would be -
so it was very obvious and easy to de-select /dev/sda or /dev/hda and choose another appropriate drive for grub to reside.

It would be *nice* to add this back in for Ubuntu 10.04 ? . . . my 2 ¢

---

### Post by Richard1979 on 2010-02-09
I agree, although it's my fault partly for not noticing it.

---

### Post by oldfred on 2010-02-09
I had this also on my desktop until I reinstall grub to sdc.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)
Slow boot, multi drives, known issue, move boot to same drive & adjust BIOS
sudo dpkg-reconfigure grub-pc

Grub installs to the first drive in BIOS unless you use the advanced tab during the install. I think they should rename that but it is assumed that you want to use grub and only advanced users would want to install it somewhere else.

I copied this from somewhere:
reinstalls grub and allows choice of which drive to install to. Choose boot drive if not sda
sudo dpkg-reconfigure grub-pc
I finally found out how to prevent the MBR to be overwritten.
I ran dpkg-reconfigure grub-pc and deselected /dev/sda which meant that the values field for grub-pc/install_devices in /var/cache/apt/config.dat is now empty. Then nothing is written to the MBR or the boot sector when grub-pc gets updated. Occasionally I should probably rerun manually grub-install /dev/sda2 after grub-pc package updates to keep stage1 install in sync.

---

### Post by presence1960 on 2010-02-09
Why don't you put GRUB on MBR of sdb, then change sdb to the first disk to boot in hard disk boot order in BIOS. Then you can boot into Ubuntu and run a command to let the updater know all grub-pc updates go to sdb.

To put GRUB on sdb MBR boot the 9.10 Live CD and choose "try ubuntu without any changes." When the desktop loads open a terminal and run ```
sudo mount /dev/sdb1 /mnt
```This will mount your / partition. Then in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```This will put GRUB on MBR of sdb. Reboot without the Live CD. Go into BIOS and set the sdb disk as first hard disk to boot. Save changes to CMOS & continue booting into ubuntu. When the desktop loads open a terminal and run ```
echo "SET grub-pc/install_devices /dev/sdb" | sudo debconf-communicate
``` This will set it up so any grub-pc updates will go to sdb.

Or as oldfred suggested ```
dpkg-reconfigure grub-pc
``` will also set up updates on sdb, providing you select sdb on the last window.

---

