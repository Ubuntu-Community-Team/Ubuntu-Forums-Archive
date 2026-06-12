---
title: "Dual Boot Issue: Restart Loop when attempt to boot into XP"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by cnugget23 on 2007-06-30
I recently tried to install a dual boot of Windows and Kubuntu Fiesty Fawn on my PC.

I can boot into Kubuntu just fine through the grub menu, however when I select to boot into Windows XP it just looks like it begins to load (white bar at bottom gets full) then my computer restarts.  I select Windows XP again and the same thing happens.

Wondering what might be going on here, and if someone can suggest some solutions.  I've been messing with this problem for a while now and have done several searches.

Here are some details you may find useful...

I have 2 disk drives on the PC...
HDD0 is just WINDOWS files (sda1 or /dev/hda1)
HDD1 has both the WIndows/Linux installations on them (sdb1 or /dev/hdb1)
boot.ini, ntldr, ntdetect.com are all on HDD1

Here is what is in my /boot/grub/menu.lst file....

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=b5e741b4-4ff2-4b79-8bcc-f1c3f682b5f3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=b5e741b4-4ff2-4b79-8bcc-f1c3f682b5f3 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b5e741b4-4ff2-4b79-8bcc-f1c3f682b5f3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b5e741b4-4ff2-4b79-8bcc-f1c3f682b5f3 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

Here is the output of >fdisk -l...

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       12161    97683201    7  HPFS/NTFS

Disk /dev/hdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        5304    42604348+   7  HPFS/NTFS
/dev/hdb2            5305        6520     9767520   83  Linux
/dev/hdb3            6521        9010    20000925   83  Linux
/dev/hdb4            9011       19929    87706867+   5  Extended
/dev/hdb5            9011        9259     2000061   82  Linux swap / Solaris
/dev/hdb6            9260       19929    85706743+   b  W95 FAT32

Here is the output of >df -Th...

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/hdb2     ext3    9.2G  3.1G  5.7G  36% /
varrun       tmpfs    506M  120K  506M   1% /var/run
varlock      tmpfs    506M     0  506M   0% /var/lock
procbususb   usbfs    506M  120K  506M   1% /proc/bus/usb
udev         tmpfs    506M  120K  506M   1% /dev
devshm       tmpfs    506M     0  506M   0% /dev/shm
lrm          tmpfs    506M   33M  473M   7% /lib/modules/2.6.20-16-generic/volatile
/dev/hdb3     ext3     19G  424M   18G   3% /home
/dev/hda1     ntfs     94G   71G   23G  76% /media/sda1
/dev/hdb1     ntfs     41G   26G   16G  63% /media/sdb1
/dev/hdb6     vfat     82G   64K   82G   1% /windows

I have HD1(sdb1) mounted to /media/sdb1 and here is output of >ls....

chrisp@BlueLinux:/media/sdb1$ ls -l
total 4632688
-r-xr-x--- 1 root plugdev          0 2002-08-08 04:02 AUTOEXEC.BAT
-r-xr-x--- 1 root plugdev        211 2006-08-23 01:21 boot.ini
dr-xr-x--- 1 root plugdev          0 2007-05-26 08:26 Config.Msi
-r-xr-x--- 1 root plugdev          0 2002-08-08 04:02 CONFIG.SYS
dr-xr-x--- 1 root plugdev       4096 2002-08-08 15:32 Documents and Settings
-r-xr-x--- 1 root plugdev 1073274880 2007-05-27 10:56 hiberfil.sys
dr-xr-x--- 1 root plugdev       4096 2006-02-13 22:34 Inetpub
dr-xr-x--- 1 root plugdev       4096 2005-09-16 11:06 Installation Files
-r-xr-x--- 1 root plugdev          0 2002-08-08 04:02 IO.SYS
-r-xr-x--- 1 root plugdev          0 2002-08-08 04:02 MSDOS.SYS
dr-xr-x--- 1 root plugdev          0 2005-07-13 17:16 MSOCache
-r-xr-x--- 1 root plugdev      47564 2005-04-13 07:33 NTDETECT.COM
-r-xr-x--- 1 root plugdev     250032 2005-04-13 07:33 ntldr
-r-xr-x--- 1 root plugdev 3670016000 2007-05-27 10:56 pagefile.sys
dr-xr-x--- 1 root plugdev      24576 2007-05-26 13:30 Program Files
dr-xr-x--- 1 root plugdev          0 2002-08-08 09:16 Recycled
dr-xr-x--- 1 root plugdev          0 2002-08-08 23:45 RECYCLER
dr-xr-x--- 1 root plugdev      57344 2007-05-27 11:40 sdwork
-r-xr-x--- 1 root plugdev       1175 2002-08-08 12:40 SETUPLOG.TXT
dr-xr-x--- 1 root plugdev          0 2007-05-27 11:07 swd
-r-xr-x--- 2 root plugdev      32768 2002-08-08 04:10 System Volume Information
dr-xr-x--- 1 root plugdev      12288 2007-05-25 06:15 TEMP
dr-xr-x--- 1 root plugdev          0 2003-09-23 18:12 Themes
dr-xr-x--- 1 root plugdev     135168 2007-05-27 10:49 WINDOWS
dr-xr-x--- 1 root plugdev          0 2004-03-01 10:45 WUTemp

Here is what boot.ini file looks like...

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

Please help me solve this issue and let me know if you need anymore info.

Thanks a ton!
-Chris

---

### Post by confused57 on 2007-06-30
Just out of curiosity, have you tried booting first to your sdb drive(I think grub is installed to the sda mbr)?
You might try removing the mapping lines in your Window's entry.
```
map (hd0) (hd1)
map (hd1) (hd0)
```

---

### Post by cnugget23 on 2007-07-01
I've tried booting into sdb1 drive first (HDD1) but that doesn't seem to work either.

Looks like grub is in sdb mbr...

>grub find /boot/grub/stage1
 (hd1,1)

Taking out the map lines from menu.lst

map (hd0) (hd1)
map (hd1) (hd0)

Gives me "NTLDR is missing" error when attempting to boot into XP.

Any other suggestions?

---

### Post by confused57 on 2007-07-01
> **cnugget23 said:**
> I've tried booting into sdb1 drive first (HDD1) but that doesn't seem to work either.

Looks like grub is in sdb mbr...

>grub find /boot/grub/stage1
 (hd1,1)

Taking out the map lines from menu.lst

map (hd0) (hd1)
map (hd1) (hd0)

Gives me "NTLDR is missing" error when attempting to boot into XP.

Any other suggestions?
I would suggest you download & burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it's a very small download & hopefully can boot into your Window's partition.

Grub itself is installed to (hd1,1), however grub's IPL is probably installed to the hda(hd0) mbr.

You could install grub's IPL to the hdb mbr, using setup (hd1):
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
This would require changing your root in menu.lst to (hd0,1) and (hd0,0) for Windows, if you booted first to hdb.  If you do decide to install grub's IPL to your hdb mbr, boot to this drive first, highlight your Ubuntu entry, press "e" to edit, highlight the root line, press "e" again, then change root from (hd1,1) to (hd0,1), press enter,  then press "b" to boot...this change is temporary, so it wouldn't affect your current setup.

It's possible that you  might be able to boot Windows with "root (hd0,0)", without the mapping lines, if you boot first to your hdb?

You probably will want to try SGD first, before considering anything else.

---

