---
title: "need help configuring Grub for 3 Os : two xp installations and ubuntu"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by AhmedW on 2008-01-16
hi everybody,

Thank u all for the great work and support u are giving in this forum

I have 3 os on 3 different partitions on one drive, two xp installations and ubuntu, I could not boot the second xp directly from grub

here is my fdisk :

```
Disque /dev/sda: 160.0 Go, 160041885696 octets
255 heads, 63 sectors/track, 19457 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30973096

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1               1        5222    41945683+   7  HPFS/NTFS
/dev/sda2   *        5223        6528    10490445    c  W95 FAT32 (LBA)
/dev/sda3            6529        9516    24001110   83  Linux
/dev/sda4            9517       19457    79851082+   f  W95 Etendu (LBA)
/dev/sda5            9517        9666     1204812   82  Linux swap / Solaris
/dev/sda6            9667       19457    78646176    b  W95 FAT32
```


sda1 has xp installed
sda2 has another xp installed
sda3 has ubuntu

here is how I configured grub menu.lst :

```

title		Windows XP number 1
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Windows XP number 2
root		(hd0,1)
savedefault
makeactive
chainloader	+1

title		Linux Ubuntu 7.10 Gusty
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ef6669c2-af96-463c-a7b6-eebece2c0467 ro quiet splash locale=fr_FR
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```


when I choose "xp number 1" from the grub menu it boots normally, but "xp number 2" won't boot and asks for system disk (ubuntu boots normally)

I can boot the second xp by configuring the boot.ini file (contained in the first partition) and choosing "xp number 1" from grub menu which will give another menu where I select the second xp ;

What I want is to boot each of the 3 os directly from grub.

I tried using grub super disk to boot the second xp from it with no success (won't boot and asks for system disk)
I also tried the option in the grub super disk that says "fix boot of windows (partition)" but without success

any help would be appreciated

---

### Post by adrian15 on 2008-01-17
> **AhmedW said:**
> 
when I choose "xp number 1" from the grub menu it boots normally, but "xp number 2" won't boot and asks for system disk (ubuntu boots normally)


This is normal. Windows is so bad designed that you need to use boot.ini in order to boot both installations and boot.ini is only found in one partition unless you install xp hiding the other xp but this is another history.

> **AhmedW said:**
> 
I also tried the option in the grub super disk that says "fix boot of windows (partition)" but without success

Which version of SGD are you using? This option is supposed to be removed from newer SGD versions due to possible copyright problems. Which SGD sub-option did you find the Fix boot of windows (partition) option in?

adrian15

---

### Post by AhmedW on 2008-01-17
Thx adrian15,

> Which version of SGD are you using? ..., Which SGD sub-option...

I'm using SGD version 0.97-os.1
downloaded it yesterday from here [http://linux-live-usb.org/download/Super_Grub_Disk/download/binaries/sgd/cdrom/sgd_0.9588.iso](http://linux-live-usb.org/download/Super_Grub_Disk/download/binaries/sgd/cdrom/sgd_0.9588.iso)

I used this SGD sub-option : Advanced > Windows(advanced) > (BETA!) Fix Boot of Windows (Partition)

> boot.ini is only found in one partition...

I also tried this:
copied all files contained in the root of first xp partition to the root of second xp partition (including boot.ini) (did not overwrite existing files)
then rebooted second xp partition from SGD, but without success.

---

