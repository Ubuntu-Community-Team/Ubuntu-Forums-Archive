---
title: "Ubuntu 10.04, Fedora 15 and windows 7"
date: 2011-08-31
forum: Installation &amp; Upgrades
---

### Post by ultimatelinux on 2011-08-31
sudo fdisk -l
[B]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf623f623

Device Boot Start End Blocks Id System
/dev/sda1 * 1 13 102400 7 HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2 13 4570 36597760 7 HPFS/NTFS
/dev/sda4 4570 19458 119586817 f W95 Ext'd (LBA)
Partition 4 does not end on cylinder boundary.
/dev/sda5 8747 19458 86032384 7 HPFS/NTFS
/dev/sda6 4570 4819 2000896 82 Linux swap / Solaris
/dev/sda7 4819 7184 18999296 83 Linux
/dev/sda8 7184 8746 12547072 83 Linux[/B]
I have windows in /dev/sda2, windows 7 created a new partition(primary) for its boot loader configuration. I've installed Ubuntu 10.04 in /dev/sda7 n /dev/sda6 is its swap. /dev/sda5 is logical drive, which I want to use to store data. I formatted /dev/sda8 with ext4 file system, now, I wish to install fedora in it, if I select installed boot loader in first sector of boot partition of fedora and then go to Ubuntu and run update-grub, will Ubuntu's grub detect fedora and will my windows be intact? 
thank you.

---

### Post by saltmarshlamb on 2011-08-31
> if I select installed boot loader in first sector of boot partition of fedora and then go to Ubuntu and run update-grub, will Ubuntu's grub detect fedora and will my windows be intact? As long as you do that then yes.

I've done similar before - no windows though - and have had no issues. You'll need to do the manual partitioning with fedora tot make sure it uses sda8 - from memory the bootloader install part is at that time as well, tell it the same partition and all will work as you expect.

Exactly what is it that you're worrying about regarding the windows install?

---

### Post by Mark Phelps on 2011-08-31
BEFORE you do anything else ... use the Win7 Backup feature to create and burn a Win7 Repair CD.  This way, if something does happen to the Win7 boot loader, at least you'll have a way of repairing it and getting access to Win7 restored.

---

### Post by YesWeCan on 2011-08-31
fedora 15 uses LVM and as long as you have LVM installed in 10.04 and you are using Grub2 you probably don't need a separate Grub for fedora at all. Ubuntu's Grub will find fedora.

You can discover your grub version using
[COLOR=Navy]grub-install -v[/COLOR]
(a version <1.0 is grub legacy and this method will not work)

Install fedora 15 and select not to install Grub at all.

Boot 10.04
[COLOR=Navy]sudo apt-get install lvm2
sudo vgchange -ay[/COLOR]
you should see fedora's LVM volumes listed
[COLOR=Navy]sudo update-grub
[COLOR=Black]you should see fedora appear in the list of detected OSs[/COLOR]
sudo grub-install /dev/sda[/COLOR]

---

