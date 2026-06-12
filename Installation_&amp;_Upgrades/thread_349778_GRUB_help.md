---
title: "GRUB help"
date: 2007-01-30
forum: Installation &amp; Upgrades
---

### Post by seanix on 2007-01-30
Hello everyone,
I'm a new convert and have a small problem with booting my Toshiba Qosmio laptop.

A few days ago, I downloaded the live cd (6.10) and booted my laptop. I liked what I saw and partitioned my first hard disk to make room for Ubuntu.
The install went fine and everything was working except that I could not boot "unless" I booted from the CD.
Windows XP and Ubuntu booted fine from the CD

here is were my problem starts.

I could not find help on how to fix this so I typed "install grub hda1" in the terminal  (or something like that ... forgot the exact command)
After that I could no longer boot any of the two operating systems.

To fix this, I booted from the Cd again and installed Ubuntu a second time. this time I added a 130MEG /boot partition to see if it would help?

Still, I can NOT boot with GRUB and the live cd will only boot Ubuntu, but not XP

What do I have to do to get XP up and running agian and how is it possible to dual boot XP and Ubuntu? It is strange that even the second time GRUB was not configured right.

I have tow hard drives in my laptop.
The first one has a total size of 60 GIG and the first 25GIG are for XP, the rest for Ubuntu
The second hard dist is 40GIG and holds various windows files

Thank you for helping :)


P.S. when I just boot the machine without the Ubuntu Live CD, the error message is: Hard Disk Error

If there's anything I can type in a terminal and post here to help with the trouble shooting, please let  me know, thanks :)

---

### Post by geek_Man on 2007-01-30
Your Windows partition might be corrupted. Hopefully it's not, but it might be. Boot with the live CD and type into the terminal "sudo fdisk -l". And post your menu.lst file.

---

### Post by seanix on 2007-01-30
Hello g_Man,
thanks for helping :)

Here is the output>>

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3315    26627706    7  HPFS/NTFS
/dev/hda2            3316        7284    31880992+   f  W95 Ext'd (LBA)
/dev/hda5            3316        7076    30210201   83  Linux
/dev/hda6            7077        7267     1534176   82  Linux swap / Solaris
/dev/hda7            7268        7284      136521   83  Linux

Disk /dev/hdb: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        4864    39070048+   7  HPFS/NTFS


I think if I could install the grub boot loader (if there is no known bug with toshiba qosmio laptops) that all would be well .... but I don't know how to do that.

Thanks :)

---

### Post by Herman on 2007-01-31
Hello seanix,
The safe way to install Grub to MBR or to the boot sector of a Linux partition or to a floppy disk or a USB disk is to use the Grub shell. The Grub shell would have given you an error message and refused to do anything when you try to write Grub to Windows bootsector. 
The grub-install command is not recommended for new users because it will do exactly as you tell it.
The hard disk's Master Boot Record (MBR), is in the first sector of the hard disk and the rest of the first track of the hard disk is usually not formatted with any file system so it does not belong to any particular operating system. It is good to install Grub there. The MBR is referred to as hda.

The first partition (hda1), does not begin until sector 63 and that is where your Windows bootsector is most commonly found in most, but not all installations. (If Windows is hda1). It is not generally a good idea to install Grub there at all, but it can be repaired. It will do no permanent damage to Windows with the FAT32 filesystem, but it might to an NTFS filesystem, but not necessarily. (You might get away with it if you are lucky).

But first, here's how to install Grub with a Grub shell:
Re-install Grub with a GRUB shell eg; with Live CD...........................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")

A few Toshiba Laptops do have a problem with Grub, I am told, because of the 'Express Media Player'. Apparently that often keeps some files in the first track of the hard disk that interfere with Grub somehow. Uninstallaing or deleting the 'Express Media Player' is reportedly sometimes necessary.

To restore your Windows bootsector, you should be able to put in your Windows XP install CD, and boot into the [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") and use the fixboot command. And keep your fingers crossed. I hope that will solve your problems and get everything working properly for you.

Good Luck !
Regards, Herman

P.S.                   TIP: You can make your own Windows XP boot floppy disk with ntldr, ntdetect, and boot.ini on it. It can boot Windows when there is no bootloader in the MBR at all, or if the bootsector is corrupted, or quite a few other problems too. For how to make your own Windows Xp boot floppy, [Click Here]("http://support.microsoft.com/kb/305595/EN-US/").

---

