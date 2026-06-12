---
title: "can you help me get grub working, please? it won't load."
date: 2006-08-07
forum: Installation &amp; Upgrades
---

### Post by ice60 on 2006-08-07
hi, i just installed Dapper over XP 8) but, i have a problem - grub doesn't load. i have a new computer with 2 SATA drives. when i boot up it mentions RAID0 STRIPE ARRAY. i have two 150GB SATA drives. but that's about all i can say.

when i try and boot it hangs saying something like - loading grub, but grub never loads!

if you can't help can you show me where the script which loads Grub is?

i just had a look at Grub and it says this near the top -

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

is there something i can edit to get grub to load?

here's one last thing, my grub menu -

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

---

### Post by ice60 on 2006-08-07
i just want to make a note of this before i lose it forever!

[http://www.ubuntuforums.org/showthread.php?t=230361](http://www.ubuntuforums.org/showthread.php?t=230361)

it says the fix is to disable RAID0 in the BIOS :D i think i can just about manage that, i hope :rolleyes: 

This is what you do:

reboot your system

select system set up

from there go down to your drives

for me I had seven or eight listed (only two active)

the last option will control what controls your hard drives....Bus System I believe....

hit enter to enable changes here

then hit your arrow keys to make your selection

I had 4 choices listed:

1. RAID Autodetect/AHCI
2. RAID Autodetect/ATA
3. RAID ON (=SATA configured for RAID on boot)
4. Combination (=SATA/PATA combo mode)

Choice # 1 was enabled.

I changed it to choice #4!

---

