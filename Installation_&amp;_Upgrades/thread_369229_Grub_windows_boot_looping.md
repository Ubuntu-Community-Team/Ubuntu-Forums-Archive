---
title: "Grub windows boot looping"
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by 14bmail on 2007-02-24
Hello there,
    I've been running ubuntu edgy + windows XP home dual boot for months. I upgraded my XP home to pro (retail) and naturally windows overwrote the MBR. I then booted with a knoppix CD and did a grub install *I do root hd0,4 as my /boot is in /dev/sda5 : i.e
grub
<inside grub>
root (hd0,4)
setup (hd0,0)
<exit + reboot>

I can boot into ubuntu fine but when I try to boot windows, it loops back into the grub loading screen. I can still boot ubuntu from there but trying to boot windows loops back to grub. I then booted the comp with XP CD, did a windows recovery and did "FIXBOOT" "FIXMBR". After a reboot, windows booted and loaded ok. So I did another knoppix reboot and did the grub install again but get the windows looping to grub error again. Does anyone know why this can happen and how to fix it? I have windows on the first partition (logical) and linux on extended as I will show some info now:

 sudo fdisk -lu
Password:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   174321314    87160626    7  HPFS/NTFS
/dev/sda2       174321315   195366464    10522575    f  W95 Ext'd (LBA)
/dev/sda5       174321378   174530159      104391   83  Linux
/dev/sda6       174530223   191269889     8369833+  83  Linux
/dev/sda7       191269953   195366464     2048256   82  Linux swap / Solaris


sda1 = windows,  sda5 = /boot, sda6 = /  and sda7 is swap

my /boot/grub/menu.lst is as follows:

default         0
timeout        10
title           Ubuntu, kernel 2.6.17-11-generic SOUND
root            (hd0,4)
kernel          /vmlinuz-2.6.17-11-generic root=/dev/sda6 ro quiet splash acpi=off
initrd          /initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic ACPI
root            (hd0,4)
kernel          /vmlinuz-2.6.17-11-generic root=/dev/sda6 ro quiet splash
initrd          /initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,4)
kernel          /vmlinuz-2.6.17-11-generic root=/dev/sda6 ro single
initrd          /initrd.img-2.6.17-11-generic
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /memtest86+.bin
quiet
boot

title           Microsoft Windows
root (hd0,0)
savedefault
chainloader +1


--end menu.lst--

I also get a couple weird things, when I try to mount /dev/sda1 (I could before the upgrade of home to Pro):

# mount /dev/sda1 1
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


And dmesg shows:
[17179696.828000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179696.856000] NTFS-fs warning (device sda1): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17179696.856000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17179696.856000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17179696.856000] NTFS-fs error (device sda1): ntfs_fill_super(): Not an NTFS volume.


*edit* just tried mount diffferently for the driver I have

mount -t ntfs-3g /dev/sda1 1
Bootsector checksum failed.
Failed to startup volume: Invalid argument
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?





Any help is appreciated with this.. thanks

---

### Post by Herman on 2007-02-24
Hello 14bmail,
I can see your problem. You are installing grub to your Windows bootsector. The MBR is (hd0), your Windows bootsector is (hd0,0)
>  grub
<inside grub>
root (hd0,4)
setup (hd0,0)
<exit + reboot> I didn't know it was possible to do that from a grub shell, whenever I try it in any of my computers I get an error message and nothing happens. I must try with Knoppix in case Knoppix's grub shell works differently. I though only people who used the grub-install command could do that.
Anyhow, the correct way to do it is this way,
```
sudo grub
``````
find /boot/grub/stage1
``````
root (hd0,4)
``````
setup (hd0)
```Probably, you can just run FIX_BOOT_ from your Windows Recovery Console once again to fix Windows _boot_sector and all will be fine.

The FIX_MBR_ command installs Windows boot code to the _MBR_.

There is a lot of bad information getting around and it is easy for people to fall into the trap of thinking Windows bootsector and the hard disk's MBR is the same thing. Many people use the term MBR and 'bootsector' interchangeably. They are not the same thing at all. The MBR is in the first sector of the hard disk, sector 0, and is not part of any filesystem.
The Windows bootsector is in the first sector of the Windows partition, wherever that is, and it is a vital part of the Windows filesystem. Most commonly it will be in sector 63. If you take a careful look at the fdisk -lu output, you will see that. 

That's why you are getting the other weird error messages too, like: > mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error That's because you are nuking you Windows first sector with code that's never supposed to go there.

The reason for it 'looping' is because when you select Windows, grub is finding the Windows bootsector alright, but that has grub in it instead of Windows bootloader code, so it points right back to grub in Ubuntu again.

I guess you can just fix your Windows bootsector again with FIXBOOT, and fix your MBR with the 'setup (hd0)', and all will be fine, with a little luck. :)

Good luck with it, and all the best,
From Herman :)

---

### Post by 14bmail on 2007-02-24
Thanks! Did the trick :D =D>

---

### Post by Herman on 2007-02-24
Alright 14bmail! :)
Way to go! :)

Just out of curiosity, I have tested 'setup (hd0,0) from a grub shell once again. I have done this several times before, and I am sure that previous times when I tried I was unable to do this. I had to resort to using grub-install to get it to actually install grub to the Windows bootsector.  I don't know if it makes any difference or not, but I tried it from a LiveCD this time, and low and behold, it has succeeded! :)
[CENTER](Don't try this at home, folks).
[/CENTER]

So the grub shell *is* able to do this, I was wrong. I apologize.

It's no problem for me, as I have the FAT32 filesystem in Windows. This will give me the boot-up error '                                 [the bootsector is not the same as its backup]("http://www.ubuntuforums.org/the%20bootsector%20is%20not%20the%20same%20as%20its%20backup")', when booting Ubuntu. And it causes grub to keep looping when I try to boot Windows. 
My computer came with a 'Recovery CD', one that restores the whole hard disk to the original condition it was in when I brought it home from the store. There is no 'Recovery Console', so I can't restore my Windows bootsector with that kind of disc. It will simply and efficiently wipe out Ubuntu, Kubuntu and Xubuntu installations. eek!
What will I do?
I will run 'sudo dosfsck -ar /dev/hda1' or 'sudo fsck -v -r /dev/hda1' from a Live CD. That's another way to fix this problem if it happens to a FAT32 filesystem. I will choose to replace the current bootsector with its backup.
[                When the bootsector is not the same as its backup]("http://users.bigpond.net.au/hermanzone/p10.htm#differences_between_the_bootsector_and_its_backup")
I have typed all this here so others who may have the same problem might find it when they do a forum search, so this thread will be even more helpful to others with the same problem. I hope it will help others to avoid this problem in the first place.

Congratulations on fixing yours, 14bmail, and well done! :)
All the best
Regards, Herman :)

---

