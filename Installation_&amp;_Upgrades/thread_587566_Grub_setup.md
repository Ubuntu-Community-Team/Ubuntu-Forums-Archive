---
title: "Grub setup"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by TimBilly on 2007-10-22
This one should be easy for you experts. I've got two hard drives - one old drive with an old copy of XP, and one shiny new drive with a Ubuntu install on it (upgraded to Gutsy today). Here's an fdisk -lu
[INDENT][FONT=Courier New]tim@Oxford:~$ sudo fdisk -lu
[sudo] password for tim:

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2a5815e1

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63    78140159    39070048+   7  HPFS/NTFS

Disk /dev/hdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x08000800

   Device    Boot      Start         End      Blocks   Id  System
/dev/hdd1 * 63   308046374   154023156   83  Linux
/dev/hdd2       308046375   312576704     2265165    5  Extended
/dev/hdd5       308046438   312576704     2265133+  82  Linux swap / Solaris[/FONT]    
[/INDENT]So yea, it's messed up. Not sure where hda went. But in any case, I need grub to see hdd1 (linux) and hdb1 (XP) as the bootable drives. Upon my first install (~1 month ago), I had a blinking cursor when I set up the linux disk as the first boot option in the BIOS. I've now gotten to the point where grub loads, gives me my options, but then gives me an ERROR 17 if I select Ubuntu and ERROR 13 if I select XP.

The workaround is to leave my Feisty live CD in the drive, let it load to the first screen, select "Boot first from hard disk" (which I think just loads grub), and then select XP or Linux. This works fine - except I have to do this every time I log off or reboot. Why does Grub work from the CD, but not from the hard disk?

Here's the tail end of menu.lst:

[INDENT][FONT=Courier New]title        Ubuntu 7.10, kernel 2.6.22-14-generic[/FONT]
[FONT=Courier New]root        (hd1,0)[/FONT]
[FONT=Courier New]kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=8f8a24b2-9261-4b85-b684-c1e86b411bac ro quiet splash[/FONT]
[FONT=Courier New]initrd        /boot/initrd.img-2.6.22-14-generic[/FONT]
[FONT=Courier New]quiet[/FONT]

[FONT=Courier New]title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)[/FONT]
[FONT=Courier New]root        (hd1,0)[/FONT]
[FONT=Courier New]kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=8f8a24b2-9261-4b85-b684-c1e86b411bac ro single[/FONT]
[FONT=Courier New]initrd        /boot/initrd.img-2.6.22-14-generic[/FONT]

[FONT=Courier New]title        Ubuntu 7.10, kernel 2.6.20-16-generic[/FONT]
[FONT=Courier New]root        (hd1,0)[/FONT]
[FONT=Courier New]kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=8f8a24b2-9261-4b85-b684-c1e86b411bac ro quiet splash[/FONT]
[FONT=Courier New]initrd        /boot/initrd.img-2.6.20-16-generic[/FONT]
[FONT=Courier New]quiet[/FONT]

[FONT=Courier New]title        Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)[/FONT]
[FONT=Courier New]root        (hd1,0)[/FONT]
[FONT=Courier New]kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=8f8a24b2-9261-4b85-b684-c1e86b411bac ro single[/FONT]
[FONT=Courier New]initrd        /boot/initrd.img-2.6.20-16-generic[/FONT]

[FONT=Courier New]title        Ubuntu 7.10, memtest86+[/FONT]
[FONT=Courier New]root        (hd1,0)[/FONT]
[FONT=Courier New]kernel        /boot/memtest86+.bin[/FONT]
[FONT=Courier New]quiet[/FONT]

[FONT=Courier New]### END DEBIAN AUTOMAGIC KERNELS LIST[/FONT]

[FONT=Courier New]# This is a divider, added to separate the menu items below from the Debian[/FONT]
[FONT=Courier New]# ones.[/FONT]
[FONT=Courier New]title        Other operating systems:[/FONT]
[FONT=Courier New]root[/FONT]


[FONT=Courier New]# This entry automatically added by the Debian installer for a non-linux OS[/FONT]
[FONT=Courier New]# on /dev/hdb1[/FONT]
[FONT=Courier New]title        Microsoft Windows XP Professional[/FONT]
[FONT=Courier New]root        (hd0,0)[/FONT]
[FONT=Courier New]savedefault[/FONT]
[FONT=Courier New]makeactive[/FONT]
[FONT=Courier New]chainloader    +1[/FONT]
[/INDENT]

---

### Post by bonestonne on 2007-10-22
it wouldn't be hdd1 for Ubuntu, it should be hda for ubuntu, and hdb for windows.
heres what my Grub looks like:

title		Ubuntu Satanic Edition x64 7.10
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7d7ab821-7b32-4de5-858d-5ab0870e65f3 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7d7ab821-7b32-4de5-858d-5ab0870e65f3 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Apple OS X
root            (hd0,0)
savedefault
makeactive
chainloader     +1

title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1
-----------------------------
with two hard drives, i'm pretty sure it would be with hda1 for a primary master and hdb1 for primary slave. partitions would be harder to specify, but partition 1 is noted as hd0,0 on my drive...but i triple boot that single drive, so there's no slave drive to change the boot list. i intend on setting up my older computer with dual boot between two drives, so i can post a boot list from that for you to look at.

Error 17 is normally associated with the partition that Grub is being used to boot from is missing or corrupt. only real way to fix that is to reinstall...but i have to say, using the live CD to get around the issue is a way i've never seen before. I have edited my boot menu though to look more user friendly [OS names, not kernel names].

i hope this helps you...but getting a Grub error 17 can only really be fixed by fully reinstalling everything on both drives. its terrible i know [i've had to do it before].

---

### Post by TimBilly on 2007-10-23
ok how stupid is this -

I switched the hard disk priority order in my BIOS, and everything works.

Previously:
1st Priority: CD-ROM (left in to boot initial Live CD screen before grub)
2nd Priority: Hard Drive
  (2a) WD hard drive (Linux)
  (2b) Maxtor hard drive (XP)
 
Now:
1st Priority: CD-ROM (no longer needed)
2nd Priority: Hard Drive
  (2a) Maxtor hard drive (XP)
  (2b) WD hard drive (Linux)

I can boot to linux or windows, all from the grub screen, or let the ticker run down and it will boot into Ubuntu just fine. I've been reading about grub, fdisk and everything, and launching with that stupid (slow) Live CD for a month. I change one seemingly unrelated thing on a whim (really I was thinking maybe grub wouldn't load and I would just boot into XP by default) and all of a sudden everything works. :-k

Oh well. Rock on.
:guitar:

---

### Post by maldojr88 on 2007-10-23
well let me teach u a lil something something while were at it...
look at the menu.lst...
and look where it says:

root(hd0,1)

well this lets you know where grub is installed...basically...
and root(hdx,y) corresponds to hdxy....

lets say hda3 would be

root(hd0,2)

where the 'a' character is 0 and the primary partitions start from 0 also

soo hdb5 is

root(hd1,4)

etc...
so in ur files u have 

root(hd1,0)

this translates to hdb1....therefore you grub is installed on the windows partition boot sector...
thats why it must go first in the BIOS order
;)
hope u learned something

---

