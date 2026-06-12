---
title: "ubuntu 10.04 freezes at boot 90% of the time"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by vaughanp on 2010-06-05
Hello all,

I have an HP Pavillion Elite HPE with intiel i7 dual boot windows 7 / ubuntu 10.04.

It usually freezes on boot up but every now and then it boots up just fine (like right now it's booted up and I'm using it to write this! )

Last night I ran the ubuntu option from the grub menu on reboot countless times, always to no avail.  And this afternoon I got lucky on my 2nd try.

Earlier yesturday I was able to reboot once and, seing my desktop booted up beautifully, I thought the problem was fixed.  Just to double check I tried rebooting again and I was stuck computerless for the evening.  (fortunately I have an old laptop to fall back on as well as a Wubi install on my windows7 partition...)

Freeze symptoms: the grub menu comes up fine.  I am able to go into windows 7 without problems.  But when I go into ubuntu it freezes after a few seconds with only a curser in the upper left corner.

here's my fdisk -l:
> 
Disque /dev/sda: 1000.2 Go, 1000204886016 octets
255 têtes, 63 secteurs/piste, 121601 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identifiant de disque : 0x1549f232

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
La partition 1 ne se termine pas sur une frontière de cylindre.
/dev/sda2              13       12744   102262756    7  HPFS/NTFS
/dev/sda3           12745      120115   862457495+   5  Etendue
/dev/sda4          120116      121602    11929600    7  HPFS/NTFS
/dev/sda5           12745      117822   844038972   83  Linux
/dev/sda6          118907      120115     9711261   82  Linux swap / Solaris
a possible issues I can think of (but not sure how to investigate further) is my gparted tells me I have a number of unallocated spaces between partitions, including at the beginning of the disk, and it is not able to eliminate them (I tried with gparted).

Any help would be appreciated.  In the meantime I'm leaving my computer ON!

---

