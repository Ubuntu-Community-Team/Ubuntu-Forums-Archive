---
title: "Problem in grub installation in P5GC-MX motherboard"
date: 2008-10-26
forum: Installation &amp; Upgrades
---

### Post by lvgandhi on 2008-10-26
I have P5GC-MX motherboard which has on one IDE hdd slot and two SATA HDD slots. I have installed primary IDE DVD drive, secondary IDE IDE HDD 80GB and Primarty SATA 160GB SATA HDD. BIOS shows  as
FIRST IDE    MASTER   DVD
FIRST IDE  SLAVE        80GB IDE DRIVE
THIRD IDE PRIMARY MASTER 160 GB SATA HDD

Debain ETCH shows 80GB IDE Drive as hdb and 160 GB SATA drive as sda.
KUBUNTU 0710 shows 80GB IDE Drive as sda and 160 GB SATA drive as sdb.

While installing Kubuntu0710 and Kubuntu0804, for grub installation I gave device as /dev/sdb11. Grub is installed rightly on /dev/sdb11. But /boot/grub/menulst stats that root as (hd1,10). But kubuntu didn't boot. When I edited this to hd0,10, it booted. Why this happens?

---

### Post by caljohnsmith on 2008-10-26
> **lvgandhi said:**
> 
While installing Kubuntu0710 and Kubuntu0804, for grub installation I gave device as /dev/sdb11. Grub is installed rightly on /dev/sdb11. But /boot/grub/menulst stats that root as (hd1,10). But kubuntu didn't boot. When I edited this to hd0,10, it booted. Why this happens?
The reason why is because Grub sees the order of drives on start up as the same as the BIOS boot order, not as the order of the drives listed in Ubuntu's /dev directory. That means on start up, the order of Grub drives is:
```
(hd0) = 1st boot drive
(hd1) = 2nd boot drive
(hd3) = 3rd boot drive
...etc.
```
Yet when you are in Ubuntu using Grub commands, then Grub sees the order of drives as the same as the /dev directory:
```
(hd0) = /dev/sda
(hd1) = /dev/sdb
(hd2) = /dev/sdc
...etc.
```
So the bottom line is, if using (hd0,10) instead of (hd1,10) worked, that means you must be booting from the sdb drive on start up, because that would make the sdb drive (hd0) on start up. Does that make sense? :)

---

### Post by lvgandhi on 2008-10-26
> **caljohnsmith said:**
> The reason why is because Grub sees the order of drives on start up as the same as the BIOS boot order, not as the order of the drives listed in Ubuntu's /dev directory. That means on start up, the order of Grub drives is:
```
(hd0) = 1st boot drive
(hd1) = 2nd boot drive
(hd3) = 3rd boot drive
...etc.
```
Yet when you are in Ubuntu using Grub commands, then Grub sees the order of drives as the same as the /dev directory:
```
(hd0) = /dev/sda
(hd1) = /dev/sdb
(hd2) = /dev/sdc
...etc.
```
So the bottom line is, if using (hd0,10) instead of (hd1,10) worked, that means you must be booting from the sdb drive on start up, because that would make the sdb drive (hd0) on start up. Does that make sense? :)

As per bios, dvd drive is 1, 80gb hdd is drive 2 and 160 gb drive where ubuntu resides is drive 3. Will this not make dvd drive sda? if so ubuntu drive should be sdc. 
If dvd drive is left out, as it is empty and then 80gb drive should be sda and ubuntu home 160gb druive is sdb. Even then it is second drive. Thus while installing second drive should be hd1. But grub while booting sees that hd0. why? I hope I made myself clear.

---

### Post by caljohnsmith on 2008-10-27
> **lvgandhi said:**
> As per bios, dvd drive is 1, 80gb hdd is drive 2 and 160 gb drive where ubuntu resides is drive 3. Will this not make dvd drive sda? if so ubuntu drive should be sdc. 
If dvd drive is left out, as it is empty and then 80gb drive should be sda and ubuntu home 160gb druive is sdb. Even then it is second drive. Thus while installing second drive should be hd1. But grub while booting sees that hd0. why? I hope I made myself clear.
You mentioned in your first post that you installed Grub to sdb11, which is the boot sector of sdb11, rather than sdb, which would be the MBR (Master Boot Record). So how is it you are booting sdb11? Are you chain loading sdb11 from some other Grub menu, or do you maybe have a Windows type MBR in sdb and have the sdb11 partition marked as active? Also, what is on the 80 GB sda drive? If it's not too much trouble, please post the output of the following:
```
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump
sudo fdisk -lu
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
grub> quit
```
That should help clarify your setup.

---

### Post by lvgandhi on 2008-10-27
> **caljohnsmith said:**
> You mentioned in your first post that you installed Grub to sdb11, which is the boot sector of sdb11, rather than sdb, which would be the MBR (Master Boot Record). So how is it you are booting sdb11? Are you chain loading sdb11 from some other Grub menu, or do you maybe have a Windows type MBR in sdb and have the sdb11 partition marked as active? Also, what is on the 80 GB sda drive? If it's not too much trouble, please post the output of the following:
```
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump
sudo fdisk -lu
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
grub> quit
```
That should help clarify your setup.

I have two HDDs. As Said in my first post, 80 gb hdd is IDE one. It is used for backup. It is connected to IDE1 as slave where as dvd drive is connected as master in IDE1.
I have SATA 160 GB drive connected SATA master. But shown in bios as IDE3 Master. 160 gb drive contains one primary ntfs partition which has winxp. Extended partition has 3 vfat partitions and 3 ext3 partitions in order. 3 ext3 partitions has debian, kubuntu0710 and kubntu0804. All linuxes had grub in their partition. All OSes are booted using GAG, a graphical boot manager. Still your grub queries yielded results as follows.
grub> find /boot/grub/stage1
 (hd1,8)
 (hd1,9)
 (hd1,10)

grub> find /grub/stage1

Error 15: File not found

gag gives to control to boot sector of partitions for booting. The above result is from kubuntu 0804.1. because of above while installing, it installs at hd1,10. but while booting, it fails unless corrected to hd0,10. this is what making me to wonder why this happens?

---

