---
title: "Grub2 Upgrade Dilemma"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by CaminoSS on 2009-12-03
Original config was Ubuntu 8.04 & Windoze Vista
Upgraded to Ubuntu 8.10 & Windoze Vista 
Upgraded again to 9.04 & Windoze Vista
Upgraded again 9.04 to 9.10 all via internet upgrade.
grub2 was not installed (grub 0.97 was maintained)
Both OS's were always available under grub
I installed grub2
grub2 was chained to grub
I could boot Ubuntu or Windoze
After running upgrade-from-grub-legacy
I lost my Windoze selection in grub2 menu
I used Vista install to execute bootrec /fixboot then bootrec /fixmbr
which disables grub completely
I then re-installed grub2 from Ubuntu CD
Then, when I ran update-grub2 I got:

Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /windows/Boot
boot: No such file or directory
done.
Of course there is no /windows/Boot directory in Ubuntu.
I cannot find in any of the grub2 files /etc/grub.d or in /etc/default/grub or grub.cfg nor in any env variable a reference to "/windows/Boot"
 
I have read through the various links on grub2
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) but no mention of this
problem or where the reference to "/windows/Boot" is coming from.

sudo fdisk -l returns:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x58000000

Device Boot Start End Blocks Id System
/dev/sda1 * 1 9982 80180383+ 7 HPFS/NTFS
/dev/sda2 9983 30401 164015617+ 5 Extended
/dev/sda5 9983 30285 163083816 83 Linux
/dev/sda6 30286 30401 931738+ 82 Linux swap / Solaris

Why does grub2 refer to "/windows/Boot"?
Where does grub2 obtain the reference to "/windows/Boot"?
How do I remove this illogical reference?
What do I need to do to get grub to find the Windoze boot loader?

Some references allude to making a separate entry in 30_os_prober
to resolve the problem but that does not address where the Windoze / Vista
loader is.

Thx in advance
Cheers....
Camino


Problems are character building events
Apparently, I'm in need of more character(s).

---

