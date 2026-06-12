---
title: "GRUB error /boot/grub/i386-pc/normal.mod"
date: 2015-03-23
forum: Installation &amp; Upgrades
---

### Post by Grem41 on 2015-03-23
Hi guys, hope someone can help

This happened once I tried to install Lubuntu Trusty Tahir 14.04 alongside another Ubuntu based distro Peppermint 3 (12.04 based) but ran into problems. This is complicated by the fact Lubuntu Trusty Tahir 14.04 seems to have wiped the original GRUB but it might be there ?
Cannot enter either of my OS as a GRUB error appears whenever I boot ie


error: file/boot/grub/i386-pc/normal.mod not found


Using the information I got from the web, I ran several commands from <grub rescue> these are to confirm the present settings so that it might help :

ls causes output
(hd0) (hd0,msdos6) (hd0,msdos5)(hd0,msdos1)


ls (hd0,msdos1) cause output
(hd0,msdos1): Filesystem is ext2


ls (hd0,msdos6) cause output
(hd0,msdos6): Filesystem is unknown


ls (hd0,msdos5) cause output
(hd0,msdos5: Filesystem is ext2


From that I think the 1 and 5 partitions being Linux file systems with 6 as swap. This makes sense as Peppermint is 1st partition with Lubuntu 5th & swap 6th as I remember but than that I'm lost. 


Thanks in advance

---

### Post by oldfred on 2015-03-23
Did you use ext2, not ext4 for partitions?

May be best to see details, I think most cases of normal.mod issues are versions of grub issues.
Run the Summary report and post link it gives:

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You may be able to use advanced mode to choose which install's grub to install to MBR. The system you use the most should have its grub in the MBR and from that boot the other install.

---

### Post by Grem41 on 2015-03-24
[SIZE=2]Thanks for the prompt reply. In answer to your questions they 

[/SIZE]
[LIST=1]
[*][SIZE=2]When I first installed the original OS (Peppermint) I think the 1st partition was ext2 and the 5th partition ext4 when I added Trusty Tahir but it's just from memory.[/SIZE]
[*][SIZE=2]Boot Repair fixs it partly & gives the following link [http://paste2.org/yxOvJvcj](http://paste2.org/yxOvJvcj)[/SIZE]
[*][SIZE=2]I will study the Advanced Options of Boot Repair and will report back.[/SIZE]
[/LIST]
[SIZE=2]
Can I just confirm my understanding here before go any further.
 
[/SIZE]
[LIST]
[*][SIZE=2]The Boot Loader GRUB2 in this case needs to be in the partition I use the most (ie [COLOR=#282828][FONT=InconsolataMedium]/dev/sda1 for Peppermint 3)
[/FONT][/COLOR][/SIZE]
[*][SIZE=2][COLOR=#282828][FONT=InconsolataMedium]Since it's there (/dev/sda1) it can be set up to access any partition (ie /dev/sda5,Trusty Tahir)
[/FONT][/COLOR][/SIZE]
[*][SIZE=2][COLOR=#282828][FONT=InconsolataMedium]Therefore I just need to add that access via 40-custom script correct ?
[/FONT][/COLOR][/SIZE]
[/LIST]
[COLOR=#282828][FONT=InconsolataMedium][SIZE=2]
Thanks again
[/SIZE] 
[/FONT][/COLOR]

---

### Post by oldfred on 2015-03-24
You only show one install in sda1.
You do not normally install grub2's boot loader to a partition but you show grub in sda1's partition.

You do not show any other install.
You have a puppy entry in the grub menu for sda3, but have no sda3 partition.
You seem to be loopmount booting the Lubuntu ISO file with grub. But the path cannot be correct.
And you normally cannot use the loopmount to install to the same partition. It says you can unmount it to use it, but I tried it and it did not work a year or two ago. I always use another drive or flash drive to loopmount.

Your loopmount shows set isofile='/home/steve/Downloads/isos/lubuntu-14.04.2-desktop-i386.iso'

But when booting from grub, no system partitions like /home or folders inside those partitions are mounted yet by the system. But /home is a default, so does that work? Other data partitions with mounts do not work.

 I currently just have a small partition on every drive for ISOs or include an ISO folder in same level as /boot. Since I use many ISO and often update them, I use a configfile entry in grub, so I just have to edit the configfile in my ISO folder and not run sudo update-grub on changes. The livecdimage.cfg is just a text file (any name you like) that looks like any grub or 40_custom file.

menuentry 'Live ISOs' {
configfile (hd0,1)/iso/livecdimage.cfg
} 

       This will boot an ISO from a hard drive or any second drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

---

