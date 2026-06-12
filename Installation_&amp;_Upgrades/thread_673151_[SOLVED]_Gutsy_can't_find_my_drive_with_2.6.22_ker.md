---
title: "[SOLVED] Gutsy can't find my drive with 2.6.22 kernel"
date: 2008-01-20
forum: Installation &amp; Upgrades
---

### Post by haaglin on 2008-01-20
I know there are som other posts about this, but none of the solutions worked for me. 

The problem is, that when running the 2.6.22-14 kernel, i get dropped into busybox with this message: 

> 
Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/9efe2541-ad83-4579-80f6-a52bb2238ed3 does not exist. Dropping to a shell !

But when booting with 2.6.20-15 kernel, everything is ok. I have tried to change the menu.lst to use root=/dev/hda1 but the same message appear. Not even the gutsy live cd can find the drive, so I had to install feisty, and then dist-upgrade to get gutsy.

---

### Post by Pumalite on 2008-01-20
You probably recently upgraded your kernel and your UUIDs don't match
Check your menu.lst against your fstab. Also run 'blkid' to confirm.

---

### Post by haaglin on 2008-01-20
The UUID in fstab and menu.lst is the same. And the 2.6.20 kernel boots with the same UUID without problem. 

> 
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9efe2541-ad83-4579-80f6-a52bb2238ed3 ro quiet splash locale=nb_NO
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
> title		Ubuntu 7.10, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=9efe2541-ad83-4579-80f6-a52bb2238ed3 ro quiet splash locale=nb_NO
initrd		/boot/initrd.img-2.6.20-15-generic
quiet

fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=9efe2541-ad83-4579-80f6-a52bb2238ed3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=12af11fa-0ab9-4be1-81d5-3b4d515bf66a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0


---

### Post by Pumalite on 2008-01-20
Try modifying the line for your problem kernel, from UUID to /dev/sd??in menu.lst

---

### Post by haaglin on 2008-01-20
> **Pumalite said:**
> Try modifying the line for your problem kernel, from UUID to /dev/sd??in menu.lst

Already tried that. The same error message appear:

> 
ALERT! /dev/hda1 does not exist. Dropping to a shell !


When dropped to shell, if i do:
```
ls /dev | grep hd
ls /dev | grep sd
```
i get nothing..

---

### Post by Pumalite on 2008-01-20
Use rescuecd: [http://sysresccd.org/Download](http://sysresccd.org/Download)
Or TestDisk: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
To check your Partition Table and the rest just to make sure

---

### Post by haaglin on 2008-01-20
> **Pumalite said:**
> Use rescuecd: [http://sysresccd.org/Download](http://sysresccd.org/Download)
Or TestDisk: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
To check your Partition Table and the rest just to make sure

Thanks. I'll try that. Just a question though, if my partition table is corrupted, why does it boot with no problem with the 2.6.20?

---

### Post by Pumalite on 2008-01-20
Good question. I asked that myself. That's why I said 'just to make sure'. We can start eliminating things.

---

### Post by haaglin on 2008-01-20
All the tools in rescuecd reported no problems with the disk or filesystem, and rescuecd had no trouble finding the disk.

---

### Post by Pumalite on 2008-01-20
Looks like an update or upgrade gone south.

---

### Post by haaglin on 2008-01-20
Yes, except that the livecd dont find the disk too. same with the alternate cd. So there must be something else. Its a pretty standard disc too 30gb Maxtor. I have used ubuntu on this disk before, but this time i wanted a fresh install, but since the livecd didn't find the disk, i installed a fresh feisty and dist-upgraded. none of the previous ubuntu versions had trouble.

---

### Post by Pumalite on 2008-01-20
Dig into your BIOS and see that your drive is well configured. I guess is an IDE? What's your motherboard and chipset?

---

### Post by haaglin on 2008-01-20
Yes, its IDE. motherboard is Asrock K7S8X. I will try to reset bios and reconfigure to see if it boots.

---

### Post by haaglin on 2008-01-20
The bios was not the problem, Still the same issue. :(

---

### Post by Pumalite on 2008-01-20
Flash your BIOS

---

### Post by haaglin on 2008-01-20
I allready have the latest bios available. Thanks for the help so far anyway ;)

---

### Post by Pumalite on 2008-01-20
Get a Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Let's see (pardon the pun)

---

### Post by haaglin on 2008-01-20
Gparted was on the rescuecd, and i tried the "check" option. It reported no errors. Is there any difference in gparted live and the one on the rescuecd?

---

### Post by Pumalite on 2008-01-20
The Live CD is probably a newer version. It can do a lot of fixing if need be.
Post your:
sudo fdisk -lu

---

### Post by haaglin on 2008-01-20
Ok. I'll boot the livecd later, here is the result of the command:
> 
Disk /dev/hda: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders, total 60058656 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe4d5e4d5

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    57496634    28748286   83  Linux
/dev/hda2        57496635    60050969     1277167+   5  Extended
/dev/hda5        57496698    60050969     1277136   82  Linux swap / Solaris


---

### Post by haaglin on 2008-01-20
I checked the versions, the gparted version on the rescuecd is the same as on the livecd

---

### Post by haaglin on 2008-01-21
*bump*

---

### Post by Pumalite on 2008-01-21
Can you see the offending kernel in Synaptic?. If you do: go for complete removal. You can reinstall later. I think is a question of path or synthaxis that we will never resolve.

---

### Post by haaglin on 2008-01-21
Ok, hopefully this may be resolved in an update sometime. Thank you for your time. Just one last thing, i have been running linux for 4 years now, but i still don't know how to split up results in terminal like the dir /p command in win. if i ls /dev, i cant see the "top" of the result.

---

### Post by Pumalite on 2008-01-21
You got me there. I use the arrows.

---

### Post by haaglin on 2008-01-22
I solved it! I replaced the ata cable, and now it boots. now another issue appears with the 2.6.22 kernel. My wlan stopped working. I'ts a Atheros 5212 chipset. It has allways worked with the restricted-drivers package, but not anymore. In the restricted drivers manager, ath_hal is marked as installed, but not in use. This is from dmesg:

> 
[   31.891984] wlan: 0.8.4.2 (0.9.3.2)
[   31.912327] ath_pci: Unknown symbol _ath_hal_attach
[   31.912412] ath_pci: Unknown symbol ath_hal_process_noisefloor
[   31.912691] ath_pci: Unknown symbol ath_hal_computetxtime
[   31.912929] ath_pci: Unknown symbol ath_hal_mhz2ieee
[   31.913020] ath_pci: Unknown symbol ath_hal_detach
[   31.913416] ath_pci: Unknown symbol ath_hal_probe
[   31.913929] ath_pci: Unknown symbol ath_hal_init_channels
[   31.914123] ath_pci: Unknown symbol ath_hal_getwirelessmodes


Any advice on this? I got it working with ndiswrapper, but the signal is not good anymore.

---

### Post by Pumalite on 2008-01-22
Try this:
sudo apt-get install linux-backports-modules-generic
Reboot
Post:
lshw -C network

---

### Post by haaglin on 2008-01-22
Backports fixed it.. Thanks!

---

### Post by Pumalite on 2008-01-22
You are welcome. Good luck.

---

