---
title: "grub errors (dpkg --configure -a) after distro upgrade 22.04.x-&gt;24.04.1"
date: 2024-10-26
forum: Installation &amp; Upgrades
---

### Post by fpiekert on 2024-10-26
Hello fellow Ubuntu users, I hope there is some swarm knowledge existing that can help me "repair" or "sort out" my issue that I have after a distro upgrade from 22.04 lts to 24.04.1 on a root server I have somewhere in cloud space.
I did the upgrade with the usual "do-release-upgrade" command as suggested/advised. Worked on another machine like a charm, but here on this one it broke something.
First, the system boots. But.
Each time I update packages or install new packages, I run into these messages:
```

root@theater:~# dpkg --configure -a
grub-pc (2.12-1ubuntu7) wird eingerichtet ...
i386-pc wird fÃ¼r Ihre Plattform installiert.
mdadm: /dev/md does not appear to be an md device
grub-install: Fehler: RAID_VERSION-Fehler (ioctl): Unpassender IOCTL (I/O-Control) fÃ¼r das GerÃ¤t.
dpkg: Fehler beim Bearbeiten des Paketes grub-pc (--configure):
 Â»installiertes post-installation-Skript des Paketes grub-pcÂ«-Unterprozess gab den Fehlerwert 1 zurÃ¼ck
dpkg: AbhÃ¤ngigkeitsprobleme verhindern Konfiguration von grub-efi-amd64-signed:
 grub-efi-amd64-signed hÃ¤ngt ab von grub-efi-amd64 | grub-pc; aber:
  Paket grub-efi-amd64 ist nicht installiert.
  Paket grub-pc ist noch nicht konfiguriert.

dpkg: Fehler beim Bearbeiten des Paketes grub-efi-amd64-signed (--configure):
 AbhÃ¤ngigkeitsprobleme - verbleibt unkonfiguriert
dpkg: AbhÃ¤ngigkeitsprobleme verhindern Konfiguration von shim-signed:
 shim-signed hÃ¤ngt ab von grub-efi-amd64-signed (>= 1.191~) | grub-efi-arm64-signed (>= 1.191~) | base-files (<< 12.3); aber:
  Paket grub-efi-amd64-signed ist noch nicht konfiguriert.
  Paket grub-efi-arm64-signed ist nicht installiert.
  Version von base-files auf dem System ist 13ubuntu10.1.
 shim-signed hÃ¤ngt ab von grub-efi-amd64-signed (>= 1.187.2~) | grub-efi-arm64-signed (>= 1.187.2~); aber:
  Paket grub-efi-amd64-signed ist noch nicht konfiguriert.
  Paket grub-efi-arm64-signed ist nicht installiert.

dpkg: Fehler beim Bearbeiten des Paketes shim-signed (--configure):
 AbhÃ¤ngigkeitsprobleme - verbleibt unkonfiguriert
Fehler traten auf beim Bearbeiten von:
 grub-pc
 grub-efi-amd64-signed
 shim-signed

```
I wonder where /dev/md comes from (without 0 / 1). Anyway. I checked installed packages for grub on both machines, appears similar:
```

root@butterfly:~# apt list --installed | grep -i grub
grub-common/noble,noble,now 2.12-1ubuntu7 amd64  [Installiert,automatisch]
grub-efi-amd64-bin/noble,noble,now 2.12-1ubuntu7 amd64  [Installiert,automatisch]
grub-efi-amd64-signed/noble,noble,now 1.202+2.12-1ubuntu7 amd64  [Installiert,automatisch]
grub-gfxpayload-lists/noble,noble,now 0.7build2 amd64  [Installiert,automatisch]
grub-pc-bin/noble,noble,now 2.12-1ubuntu7 amd64  [Installiert,automatisch]
grub-pc/noble,noble,now 2.12-1ubuntu7 amd64  [installiert]
grub2-common/noble,noble,now 2.12-1ubuntu7 amd64  [Installiert,automatisch]

```
and files are in the corresponding /boot/** dirs
```

root@theater:/etc# l /boot/
insgesamt 177740
drwxr-xr-x  5 root root     4096 Okt 21 06:59 ./
drwxr-xr-x 22 root root     4096 Okt 26 00:23 ../
-rw-r--r--  1 root root   287493 Aug 30 10:32 config-6.8.0-45-generic
-rw-r--r--  1 root root   287493 Sep 27 19:21 config-6.8.0-47-generic
drwxr-xr-x  3 root root     4096 Okt  9 10:30 efi/
drwxr-xr-x  6 root root     4096 Okt 17 06:05 grub/
lrwxrwxrwx  1 root root       27 Okt 17 06:05 initrd.img -> initrd.img-6.8.0-47-generic
-rw-r--r--  1 root root 66639061 Okt  6 12:04 initrd.img-6.8.0-45-generic
-rw-r--r--  1 root root 66709477 Okt 21 06:59 initrd.img-6.8.0-47-generic
lrwxrwxrwx  1 root root       27 Okt  6 11:32 initrd.img.old -> initrd.img-6.8.0-45-generic
drwx------  2 root root    16384 Dez 22  2022 lost+found/
-rw-------  1 root root  9061992 Aug 30 10:32 System.map-6.8.0-45-generic
-rw-------  1 root root  9061992 Sep 27 19:21 System.map-6.8.0-47-generic
lrwxrwxrwx  1 root root       24 Okt 17 06:05 vmlinuz -> vmlinuz-6.8.0-47-generic
-rw-------  1 root root 14948744 Aug 30 11:02 vmlinuz-6.8.0-45-generic
-rw-------  1 root root 14956936 Sep 27 20:47 vmlinuz-6.8.0-47-generic
lrwxrwxrwx  1 root root       24 Okt  6 11:32 vmlinuz.old -> vmlinuz-6.8.0-45-generic
root@theater:/boot# l grub/
insgesamt 2412
drwxr-xr-x 6 root root    4096 Okt 17 06:05 ./
drwxr-xr-x 5 root root    4096 Okt 21 06:59 ../
-rw-r--r-- 1 root root     120 Jan  2  2024 device.map
drwxr-xr-x 2 root root    4096 Okt 10  2023 fonts/
-rw-r--r-- 1 root root     712 Okt  6 12:04 gfxblacklist.txt
-rw-r--r-- 1 root root    9599 Okt 17 06:05 grub.cfg
-rw-r--r-- 1 root root    1024 Okt  6 12:10 grubenv
drwxr-xr-x 2 root root   20480 Jan  2  2024 i386-pc/
drwxr-xr-x 2 root root    4096 Jan  2  2024 locale/
-rw-r--r-- 1 root root 2392289 Okt 10  2023 unicode.pf2
drwxr-xr-x 2 root root   12288 Okt 10  2023 x86_64-efi/

```
Checking now existing drive devices shows
```

root@theater:~# cat /proc/mdstat
Personalities : [raid1] [raid0] [raid6] [raid5] [raid4] [raid10]
md1 : active raid1 sdb4[1] sda4[0]
      463692800 blocks super 1.2 [2/2] [UU]
      bitmap: 4/4 pages [16KB], 65536KB chunk

md0 : active raid1 sdb2[1] sda2[0]
      1022976 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>
root@theater:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
LABEL=root      /       ext4    defaults        1       1
LABEL=swap0     none    swap    defaults        0       0
LABEL=swap1     none    swap    defaults        0       0
LABEL=boot      /boot   ext4    defaults        1       2

```
This machine is EFI/Secure Boot capable, but it is not used. I have a similar hardware machine which was 24.04.1 out of the box installed. I see the required files under /boot/efi/** but no efi boot according to efibootmgr. So I assume this problematic machine doesn't need to have an efi way of booting either, right?
I am stuck, to put it plainly, on what to do now - except reinstall directly to 24.04.1. Maybe there is a similar reliable way of getting things working again, e.g. properly fix the configuration issues.
I hope someone has knowledge - the google findings didn't help me.
And no, the hosting company support isn't helpful either - been thru that request.

---

