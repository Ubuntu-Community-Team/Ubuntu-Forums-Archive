---
title: "anyone know how to triple boot?"
date: 2006-05-02
forum: Installation &amp; Upgrades
---

### Post by groggyboy on 2006-05-02
so I currently have windows xp and ubuntu dapper running in peaceful dual-boot harmony on my deck.  ubuntu is my first taste of linux, and what a nice taste!  now, call me curious, call me reckless, but I've gotten it into my head to try out another distro - right now I'm leaning towards gentoo, just cuz it'd be a great learning experience.

i use GRUB (of course), installed in /boot on my ubuntu partition.
this is my partition table (a bit messy, but tidying it up would require a sh*tload of work):

/dev/sda1 - 60 meg, FAT16 - dellutility (it came preinstalled by dell)
/dev/sda2 - 12 gig, NTFS - windows
/dev/sda4 - 12 gig, ext3 - ubuntu
/dev/sda3 - extended partition
   /dev/sda7 - 2.25 gig, ext3 - /home
   /dev/sda5 - 28 gig, FAT32 - osshare (music, video, etc, for use in either OS)
   /dev/sda6 - 1.5 gig, swap - linux swap

now, i can shave five gigs off either my ubuntu or my osshare partition to make room for gentoo.  but i'm concerned about GRUB and about the gentoo installer - do i need to set up a seperate /boot partition for grub, or can it stay where it is?  i hope gentoo doesn't try to take over boot-up control!

anyone think they can help me, or know of any useful websites?
cheers, groggyboy

---

### Post by tonyr on 2006-05-02
Here's a page of screenshots with Gentoo Installer steps.  
[URL="http://www.gentoo.org/proj/en/releng/installer/screenshots/"]
http://www.gentoo.org/proj/en/releng/installer/screenshots/[/URL]
The bootloader step has a selection for **None**, so I guess you can skip 
the bootloader installation, save yourself some grief, and modify your 
existing grub menu file accordingly.

---

### Post by openmind on 2006-05-02
I'm " Quad" booting on another box (Win, Mepis, Arch and Dapper). The way I do it is long-winded but foolproof, load Win first, add another partition add Mepis, deny loading of boot manager, add another partition, load Arch, deny loading of boot manager, add another partition, load Ubuntu, Load Grub, it finds the others and Bingo!

But seeing as you already have Win and Ubuntu working together, it's probably best to manually configure Grub after install.

---

### Post by groggyboy on 2006-05-02
cool.  so gentoo won't try taking control of the boot up.  that's good to know.

it's this whole manually editing grub thing that i'm still a little worried about.  would running "sudo update-grub" or somesuch command automatically point grub to the new gentoo partition?  or could I just reinstall grub in ubuntu (via the install disc, lets say)?

if not, what would the new grub entry look like?  I imagine something like this (correct me if I'm wrong, please):> title           Gentoo
root            (hd0,6) *<-- saying the partition is third in the extended partition, after osshare*
kernel          /boot/vmlinuz-2.6.16-386 root=/dev/sda8 ro
initrd          /boot/initrd.img-2.6.16-386
savedefault
chainloader +2 *<-- windows is currently chainloader +1 in my grub file*


---

### Post by aysiu on 2006-05-02
I use to boot about five different distros on one hard drive.

Openmind's instructions are the way to go.

---

### Post by tonyr on 2006-05-02
[QUOTE=groggyboy]cool.  so gentoo won't try taking control of the boot up.  that's good to know.

it's this whole manually editing grub thing that i'm still a little worried about.  would running "sudo update-grub" or somesuch command automatically point grub to the new gentoo partition?  or could I just reinstall grub in ubuntu (via the install disc, lets say)?

if not, what would the new grub entry look like?  I imagine something like this (correct me if I'm wrong, please):[/QUOTE]

You don't need the **chainloader +2** part.  **chainloader** is used to 
get into the Win boot stuff, a different animal altogether.  Actually, you don't
need very much at all.  Here is the menu.lst from my desktop (several
Mandriva's, Win98[don't ask], WinXP):
```

# By default, boot the third entry.
default 2

# Boot automatically after 30 secs.
timeout 30

# Fallback to the second entry.
fallback 1

#for booting linux Mandrake 9.1
title Mandrake91
root (hd1,2)
kernel (hd1,2)/boot/vmlinuz root=/dev/hdb3

#for booting the Mandrake 10.1 Official
title Mandrake10.1
root (hd1,7)
kernel (hd1,7)/boot/vmlinuz root=/dev/hdb8

#for booting the Mandriva 10.2 Official
title Mandriva10.2
root (hd1,8)
splashimage (hd1,8)/boot/grub/mdv-grub_splash.xpm.gz 
kernel (hd1,8)/boot/vmlinuz root=/dev/hdb9

#for booting Windows XP/W98
title windows
root (hd0,0)
chainloader +1


```

All Win OS are on the first drive (hda, or hd0 for grub). All *nixen are on the
second drive, hdb (or hd1 for grub).  As I added more Mandriva releases, I
simply copied the previous menu entry lines and modified as necessary,
root, kernel name and root partition device.

---

