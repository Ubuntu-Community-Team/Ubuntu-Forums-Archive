---
title: "Booting Ubuntu from new USB key"
date: 2015-02-21
forum: Installation &amp; Upgrades
---

### Post by mboisson on 2015-02-21
Hi,
I had installed Ubuntu on a bootable USB key (Lexar, 8GB) because I use the disks on that server only for the data (on a Raid-Z). Since 8 GB was becoming to little space, I bought a 32 GB USB key (Sandisk Ultra). I created the partitions (1 bootable ext4 and 1 swap) on the key, used a live CD to rsync the root partition from the 8 GB key to the 32 GB key, and reinitialized grub from a chroot. I rebooted with only the 32 GB key in. It is seen by the bios, and is bootable, since Grub starts from it. 

However, grub itself does not see the key (which is ironic, since it is installed on it). What I mean by that is that the key does not show up in /dev/disks/by-uuid (or any /dev/disks/* for that matter). Therefore, grub complains that /dev/disks/by-uuid/... which is listed in the fstab does not exist and does not want to start Ubuntu. 

The 32 GB key does show up in /dev/disk/by-uuid if I boot through the 8 GB drive and Ubuntu gets started, but it seems that grub itself won't see it.

Any idea how to fix this ?

Note : this is Ubuntu 14.04.1 LTS with all updates installed.

Thanks

---

### Post by fantab on 2015-02-21
Your new '/' partiion on 32gb drive will have a different UUID than the 8gb partition.
You will have to edit the /etc/fstab file as root and change the '/' partition's UUID to that of 32gb disk.
```
sudo blkid
```
run from live media, with 32gb usb plugged in should tell give you the UUID of the partition is question. You may also have to change the UUID of the swap partiion.

---

### Post by oldfred on 2015-02-21
Because you used rsync and created partitions in advance, you probably have a mis-match of UUID.
That will be in the grub.cfg and fstab and a few other places like reinstall of grub and perhaps a few other places. 
I normally suggest a clean install, copy /home and maybe copy some of /etc if you have modified system wide settings manually and you have exactly same version. 

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

You may be able to edit fstab with correct UUID, and just the one entry for booting in the the grub.cfg file that we do not edit. You are an exception to the rule. But once you boot and run sudo update-grub it will reset all entries in grub.cfg to be correct UUIDs. You could also have issues with drive number. When you installed it become something other than hd0, but when you boot the default from BIOS is always hd0, so you may need to also manually edit that. The search by UUID should override that, but if UUID is wrong then nether setting is correct.

---

### Post by mboisson on 2015-02-21
Hi,
Thanks for the answers, but that is not it. The correct new UUID have been put in the fstab, and I have reconfigured grub from within a chroot to the new / partition. The problem is that the USB drive is NOT DETECTED by grub. Yes, Grub cannot find the /dev/disks/by-uuid/...  but NOT because it has the wrong UUID, because there are no UUID to be found at all. That is Grub does not detect as a device the USB drive on which it is installed itself :

ls -lh /dev/disk/ :
total 0
drwxr-xr-x 2 root root 580 Feb 18 20:05 by-id

ls -lh /dev/disk/by-id/ :
total 0
lrwxrwxrwx 1 root root  9 Feb 18 20:04 ata-HL-DT-ST_DVD-ROM_GDR-H30N -> ../../sr0
lrwxrwxrwx 1 root root  9 Feb 18 20:04 ata-WDC_WD20EZRX-00D8PB0_WD-WMC4M2152254 -> ../../sda
lrwxrwxrwx 1 root root 10 Feb 18 20:04 ata-WDC_WD20EZRX-00D8PB0_WD-WMC4M2152254-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Feb 18 20:04 ata-WDC_WD20EZRX-00D8PB0_WD-WMC4M2152254-part2 -> ../../sda2
lrwxrwxrwx 1 root root  9 Feb 18 20:04 ata-WDC_WD20EZRX-00D8PB0_WD-WMC4M2612840 -> ../../sdc
lrwxrwxrwx 1 root root 10 Feb 18 20:04 ata-WDC_WD20EZRX-00D8PB0_WD-WMC4M2612840-part1 -> ../../sdc1
lrwxrwxrwx 1 root root 10 Feb 18 20:04 ata-WDC_WD20EZRX-00D8PB0_WD-WMC4M2612840-part2 -> ../../sdc2
lrwxrwxrwx 1 root root  9 Feb 18 20:04 ata-WDC_WD20EZRX-00DC0B0_WD-WCC300448071 -> ../../sdb
lrwxrwxrwx 1 root root 10 Feb 18 20:04 ata-WDC_WD20EZRX-00DC0B0_WD-WCC300448071-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Feb 18 20:04 ata-WDC_WD20EZRX-00DC0B0_WD-WCC300448071-part2 -> ../../sdb2
lrwxrwxrwx 1 root root  9 Feb 18 20:04 wwn-0x50014ee2b34130ff -> ../../sdb
lrwxrwxrwx 1 root root 10 Feb 18 20:04 wwn-0x50014ee2b34130ff-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Feb 18 20:04 wwn-0x50014ee2b34130ff-part2 -> ../../sdb2
lrwxrwxrwx 1 root root  9 Feb 18 20:04 wwn-0x50014ee659938cc2 -> ../../sda
lrwxrwxrwx 1 root root 10 Feb 18 20:04 wwn-0x50014ee659938cc2-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Feb 18 20:04 wwn-0x50014ee659938cc2-part2 -> ../../sda2
lrwxrwxrwx 1 root root  9 Feb 18 20:04 wwn-0x50014ee6aee8a1e4 -> ../../sdc
lrwxrwxrwx 1 root root 10 Feb 18 20:04 wwn-0x50014ee6aee8a1e4-part1 -> ../../sdc1
lrwxrwxrwx 1 root root 10 Feb 18 20:04 wwn-0x50014ee6aee8a1e4-part2 -> ../../sdc2

All those devices are the physical disks, (and the CD-rom) not the USB drive.

---

### Post by mboisson on 2015-02-21
Once I'm booted with the 8GB drive, in Ubuntu, if I mount the 32GB drive partition, here is what I get : 
mboisson@htpc:~$ ls -lh /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 Feb 18 20:04 96623fd6-1665-4793-a501-8098bb0cf674 -> ../../sdd5
lrwxrwxrwx 1 root root 10 Feb 18 20:04 975f67a5-7948-4b8e-b475-c5286c73bb1a -> ../../sdd1
lrwxrwxrwx 1 root root 10 Feb 18 20:05 cc79b036-5860-4852-948a-9c2e86629ea3 -> ../../sde1
lrwxrwxrwx 1 root root 10 Feb 18 20:05 fb2bf79c-130c-44b9-97f8-4678a4fa4519 -> ../../sde5

mboisson@htpc:~$ mount | grep sde
/dev/sde1 on /mnt/new type ext4 (rw)

mboisson@htpc:~$ cat /mnt/new/etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd1 during installation
#UUID=975f67a5-7948-4b8e-b475-c5286c73bb1a /               ext4    errors=remount-ro 0       1
UUID=cc79b036-5860-4852-948a-9c2e86629ea3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd5 during installation
#UUID=96623fd6-1665-4793-a501-8098bb0cf674 none            swap    sw              0       0
UUID=fb2bf79c-130c-44b9-97f8-4678a4fa4519 none            swap    sw              0       0

You can see the old UUIDs are commented, and the new UUIDs are correct. 

The new UUID has also been put in grub.cfg by update-grub : 
mboisson@htpc:~$ grep uuid /mnt/new/boot/grub/grub.cfg 
  search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos1 --hint-efi=hd3,msdos1 --hint-baremetal=ahci3,msdos1  cc79b036-5860-4852-948a-9c2e86629ea3
  search --no-floppy --fs-uuid --set=root cc79b036-5860-4852-948a-9c2e86629ea3
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos1 --hint-efi=hd3,msdos1 --hint-baremetal=ahci3,msdos1  cc79b036-5860-4852-948a-9c2e86629ea3
	  search --no-floppy --fs-uuid --set=root cc79b036-5860-4852-948a-9c2e86629ea3
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos1 --hint-efi=hd3,msdos1 --hint-baremetal=ahci3,msdos1  cc79b036-5860-4852-948a-9c2e86629ea3
		  search --no-floppy --fs-uuid --set=root cc79b036-5860-4852-948a-9c2e86629ea3
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos1 --hint-efi=hd3,msdos1 --hint-baremetal=ahci3,msdos1  cc79b036-5860-4852-948a-9c2e86629ea3
		  search --no-floppy --fs-uuid --set=root cc79b036-5860-4852-948a-9c2e86629ea3
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos1 --hint-efi=hd3,msdos1 --hint-baremetal=ahci3,msdos1  cc79b036-5860-4852-948a-9c2e86629ea3
		  search --no-floppy --fs-uuid --set=root cc79b036-5860-4852-948a-9c2e86629ea3
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos1 --hint-efi=hd3,msdos1 --hint-baremetal=ahci3,msdos1  cc79b036-5860-4852-948a-9c2e86629ea3
		  search --no-floppy --fs-uuid --set=root cc79b036-5860-4852-948a-9c2e86629ea3
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos1 --hint-efi=hd3,msdos1 --hint-baremetal=ahci3,msdos1  cc79b036-5860-4852-948a-9c2e86629ea3
	  search --no-floppy --fs-uuid --set=root cc79b036-5860-4852-948a-9c2e86629ea3
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos1 --hint-efi=hd3,msdos1 --hint-baremetal=ahci3,msdos1  cc79b036-5860-4852-948a-9c2e86629ea3
	  search --no-floppy --fs-uuid --set=root cc79b036-5860-4852-948a-9c2e86629ea3

---

### Post by oldfred on 2015-02-21
Still try changing hd3 to hd0. The search by UUID should overwrite that, but it may need help.
Boot drive is always hd0.

Your are showing default as hd3:
hint-bios=hd3,msdos1

---

### Post by sudodus on 2015-02-21
> **mboisson said:**
> Hi,
I had installed Ubuntu on a bootable USB key (Lexar, 8GB) because I use the disks on that server only for the data (on a Raid-Z). Since 8 GB was becoming to little space, I bought a 32 GB USB key (Sandisk Ultra). I created the partitions (1 bootable ext4 and 1 swap) on the key, used a live CD to rsync the root partition from the 8 GB key to the 32 GB key, and reinitialized grub from a chroot. I rebooted with only the 32 GB key in. It is seen by the bios, and is bootable, since Grub starts from it. 

However, grub itself does not see the key (which is ironic, since it is installed on it). What I mean by that is that the key does not show up in /dev/disks/by-uuid (or any /dev/disks/* for that matter). Therefore, grub complains that /dev/disks/by-uuid/... which is listed in the fstab does not exist and does not want to start Ubuntu. 

The 32 GB key does show up in /dev/disk/by-uuid if I boot through the 8 GB drive and Ubuntu gets started, but it seems that grub itself won't see it.

Any idea how to fix this ?

Note : this is Ubuntu 14.04.1 LTS with all updates installed.

Thanks

If I remember correctly, another user at the Ubuntu Forums described a similar problem some weeks ago (also with a big and new Sandisk Ultra, that refused to boot). Maybe the problem is that it is a bad booter. See the following threads

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)
[This link shows a bootability test in January 2014]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907221#post12907221"). 

I suggest that you try some fundamental things in order to find out if the computer can boot at all from the 32 GB Sandisk Ultra.

Use ***mkusb*** to make a USB boot drive from an iso file, for example your Ubuntu 14.04.1 LTS iso file.

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

1. ***If this works*** (you can boot from it), we know that the computer can boot from the pendrive. You should spend some time to really test that it works (and it should work with the same settings that work with the 8 GB pendrive).

The next step is to make your installed system again, and you might try another method to do it, for example ***cloning*** the whole 8 GB pendrive, and expanding the file system afterwards (with ***gparted***). See this link

[GrowIt.pdf]("http://phillw.net/isos/linux-tools/9w/GrowIt.pdf") 

2. ***Otherwise*** we know that your Sandisk Ultra 32 GB cannot boot, at least not in your computer, and you are not likely to succeed. The problem might be that the BIOS/UEFI system or some firmware or hardware is not compatible with that particular pendrive. My experience is that Sandisk ***Extreme*** works in most computers. It is also a fast pendrive, that works well with installed systems.

---

### Post by sudodus on 2015-02-21
I found the thread: [clone os on flash drive won't boot]("http://ubuntuforums.org/showthread.php?t=2260821")

I did not remember correctly, it was a ***Sandisk****** Fit (32 GB)***, that did not boot, but under the hood your 32 GB pendrive might be similar (the interface to USB). So I think it is worthwhile testing if it is bootable with a system, that you can be rather sure, that it works (like I suggested in the previous link).

---

### Post by mboisson on 2015-02-21
Hi,
Isn't the fact that Grub starts a proof that my system can boot with the pendrive ? Afterall, Grub is installed on the pendrive, and Grub does start when I indicate through my bios to boot from this drive. It just drops to initramfs after not being able to find the very drive from which it is itself running.

---

### Post by mboisson on 2015-02-21
Note that there is no other bootable drive with grub installed on this system. All 3 drives are used for a ZFS raid that is host to my /home.

---

### Post by oldfred on 2015-02-21
Some have found waiting a bit and then pressing enter works.

If initramfs does that have to be rebuilt? It should not have to be.

Chroot again and run these commands, if chroot sudo not required:
 apt-get dist-upgrade
dpkg --configure -a

   sudo update-initramfs -k all -c
sudo update-grub

---

### Post by sudodus on 2015-02-22
> **mboisson said:**
> Hi,
Isn't the fact that Grub starts a proof that my system can boot with the pendrive ? Afterall, Grub is installed on the pendrive, and Grub does start when I indicate through my bios to boot from this drive. It just drops to initramfs after not being able to find the very drive from which it is itself running.

> **mboisson said:**
> Note that there is no other bootable drive with grub installed on this system. All 3 drives are used for a ZFS raid that is host to my /home.

Yes, that should be proof enough, that you are booting from the pendrive, and that the problem is in the configuration.

---

