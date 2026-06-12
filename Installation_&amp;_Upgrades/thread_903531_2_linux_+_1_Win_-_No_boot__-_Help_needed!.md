---
title: "2 linux + 1 Win - No boot  - Help needed!"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by Vadko on 2008-08-28
Hello,

I tryed to install Ubuntu 8.04, Kwort Linux 2.4 and Win XP pro.
Win XP is on a disk by itself (sdb), and both linux distros and one ntfs partition on other disk (sda).
I installed the OSes in the following order: 1st Win XP, 2nd Kwort, 3rd Ubuntu.
The system boots directly to Win, neither LILO (kwort) was installed, nor  GRUB (Ubuntu).

What I've tryed:

1st - Using Supergrub CD to install grub (parameters below), all went fine the machine booted to GRUB presentin the menu, but none of the OS booted when selected - Linux distros always saying 'no such partition' and Win 'failed to load NTLDR(?) press Ctrl+Alt+Del to reboot'

2nd - Fixed Win MBR and the sistem booted fine to WinXP

3rd - Using Supergrub CD I tried to boot from all partitions that showed on the menu and none(!) booted any of the linux distros only Win XP!

4th - Used Ubuntu LiveCD to see if the partitions were there and all partitions and filesystems were there(!), with Gparted I flagged /dev/sdb3 as 'boot' hoping that at least ubuntu would boot, the I repeated the 1st step - the same results occurred, GRUB installed fine but no OS booted!

5th - Tried everything I could with Supergrub CD with no results!

6th - Tried all the above steps with only Win XP and Ubuntu 8.04 LTS with the same results 

I don't know what to do anymore! Please some Help.

Below are the disk partitions and GRUB parameteres:

Device     Boot      Start         End      Blocks   Id  System

/dev/sda2               1        8510    68356543+   7  HPFS/NTFS
/dev/sda3   *        8511        8998     3919860   83  Linux
/dev/sda4            8999        9484     3903795   83  Linux
/dev/sda1            9485        9733     2000092+   5  Extended
   /dev/sda5            9485        9733     2000061   82  Linux swap / Solaris


/dev/sdb1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sdb2            6375       14945    68846557+   f  W95 Ext'd (LBA)
/dev/sdb5            6375       14945    68846526    7  HPFS/NTFS



## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=668604e2-da10-4059-8f90-f2de5ad38f5f ro quiet splash locale=pt_PT
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=668604e2-da10-4059-8f90-f2de5ad38f5f ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title		Linux (on /dev/sda4)
root		(hd0,3)
kernel		/boot/vmlinuz root=/dev/hdd4 ro vga = normal 
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by louieb on 2008-08-29
Is one drive IDE and one SATA?
If so then you have GRUB install confusion. Its guessing wrong which drive boots 1st. This thread has the steps you need to go through for the fix. [Dualboot Two Hard Drives - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=179902")

---

### Post by Vadko on 2008-09-01
This last post helped a bit.

The problem is fixed. I tryed 2 solutions and both worked:

1st solution
Installed Wingrub GUI and made the NTLDR give me te option to boot Win or the Grub list. When Win is choosed it loads with no problems.
When the grub option is loaded, I can boot both linux distros. The list also show WinXP as an option but doesn't load it(NTLDR missing!) 

2nd solution
With Supergrub CD I  fixed the win boot @ hdb mbr (SATA) and installed grub @ hda mbr (IDE)...in the bios changed the primary boot from hdb to hda and also worked.

Thanks to those who replyed, hope this thread help those with similar problems.

---

